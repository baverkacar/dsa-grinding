# Question Link
https://leetcode.com/problems/can-place-flowers/

# Code

```java
class Solution {
    public boolean canPlaceFlowers(int[] flowerbed, int n) {

        for(int index = 0; index < flowerbed.length; index++) {
            if (flowerbed[index] == 0) {
                boolean leftPlace = (index == 0 || flowerbed[index - 1] == 0);  
                boolean rightPlace = (index == flowerbed.length - 1 || flowerbed[index+1]== 0); 

                if(leftPlace && rightPlace) {
                    n--;
                    flowerbed[index] = 1;
                } 
            }
        }
        return n<=0;
    }
}
```