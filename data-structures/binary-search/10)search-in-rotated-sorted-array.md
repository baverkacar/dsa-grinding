# Question Link

https://leetcode.com/problems/search-in-rotated-sorted-array/

# Code
Java:
```java

class Solution {
    public int search(int[] nums, int target) {
        int l = 0;
        int r = nums.length - 1;

        while (l < r) {
            int mid = l + (r-l) / 2;
            if(nums[mid] > nums[r]) {
                l = mid + 1;
            }
            else if(nums[mid] < nums[r]) {
                r = mid;
            }
        }

        if(target == nums[l]) {
            return l;
        }
        
        int pivot = l;
        l = 0;
        r = nums.length - 1;
        int a = findTarget(l, pivot - 1, target, nums);
        int b = findTarget(pivot + 1, r, target, nums);

        return Math.max(a, b);
    }

    private int findTarget(int l, int r, int target, int[] nums) {
        while (l <= r) {
            int mid = l + (r - l) / 2;

            if (nums[mid] == target) {
                return mid; // target found
            } 
            else if (nums[mid] < target) {
                l = mid + 1; // search in right half
            } 
            else {
                r = mid - 1; // search in left half
            }
        }
        return -1;
    }
}
```

Golang:
```go
func search(nums []int, target int) int {
    l, r := 0, len(nums)-1

    for l < r {
        mid := l + (r-l)/2
        if nums[mid] > nums[r] {
            l = mid + 1
        } else if nums[mid] < nums[r] {
            r = mid
        }
    }

    if target == nums[l] {
        return l
    }

    pivot := l
    l = 0
    r = len(nums) - 1
    a := findTarget(l, pivot-1, target, nums)
    b := findTarget(pivot+1, r, target, nums)

    if a > b {
        return a
    }
    return b
}

func findTarget(l, r, target int, nums []int) int {
    for l <= r {
        mid := l + (r-l)/2

        if nums[mid] == target {
            return mid // target found
        } else if nums[mid] < target {
            l = mid + 1 // search in right half
        } else {
            r = mid - 1 // search in left half
        }
    }
    return -1
}
```

# Complexity Analysis
- Time complexity: O(log n) where n is the number of elements in the array. The binary search approach reduces the search space by half in each iteration.
- Space complexity: O(1) as we are using constant extra space.