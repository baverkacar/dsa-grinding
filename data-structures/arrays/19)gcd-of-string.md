# Question Link
https://leetcode.com/problems/greatest-common-divisor-of-strings/

# Code

Java:
```java

class Solution {

    // This method calculates the Greatest Common Divisor (GCD)
    // of two integers using the Euclidean algorithm.
    public int gcd(int x, int y) {

        // Example: gcd(6, 4)
        // Step 1 → gcd(6, 4)
        // Step 2 → gcd(4, 2)
        // Step 3 → gcd(2, 0) → return 2

        if (y == 0) {              
            // ① Base case: when the second number becomes 0,
            // it means we’ve found the greatest common divisor.
            // Return x as the GCD result.
            return x;              
        } else {                   
            // ② Recursive step: call gcd(y, x % y)
            // The modulo (%) operation gives the remainder
            // of dividing x by y.
            //
            // Example:
            // gcd(6, 4) → gcd(4, 6 % 4) → gcd(4, 2)
            // gcd(4, 2) → gcd(2, 4 % 2) → gcd(2, 0)
            // Then y = 0 → return 2
            return gcd(y, x % y);  
        }    
    }

    // This method finds the "GCD String" (the largest common repeating pattern)
    // between two given strings.
    public String gcdOfStrings(String str1, String str2) {

        // Step 1: Check if the strings are compatible.
        // The concatenation str1 + str2 must be equal to str2 + str1
        // for them to share the same base pattern.
        //
        // Example:
        // str1 = "ABABAB", str2 = "ABAB"
        // str1 + str2 = "ABABABABAB"
        // str2 + str1 = "ABABABABAB" → same ✅
        //
        // If not equal, it means they don’t share a common pattern → return ""
        if (!(str1 + str2).equals(str2 + str1)) {
            return "";
        }
        
        // Step 2: Find the GCD of their lengths.
        // str1.length() = 6, str2.length() = 4 → gcd(6, 4) = 2
        int gcdLength = gcd(str1.length(), str2.length());

        // Step 3: Take the first gcdLength characters from str1.
        // str1.substring(0, 2) → "AB"
        //
        // This substring is the common repeating unit between both strings.
        return str1.substring(0, gcdLength);
    }
}
```
Golang
```go
func gcdOfStrings(str1 string, str2 string) string {
	if str1+str2 != str2+str1 {
		return ""
	}
	gcdLength := gcd(len(str1), len(str2))
	return str1[:gcdLength]
}

func gcd(a, b int) int {
	if b == 0 {
		return a
	}
	return gcd(b, a%b)
}
```

# Complexity Analysis
- Time complexity: O(n + m) where n and m are the lengths of str1 and str2 respectively. The concatenation and comparison take O(n + m) time, and finding the GCD of the lengths takes O(log(min(n, m))) time, which is dominated by the concatenation step.
- Space complexity: O(n + m) for storing the concatenated strings during the comparison. The space used for the GCD calculation is O(1).
