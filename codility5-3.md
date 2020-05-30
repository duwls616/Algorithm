# MinAvgTwoSlice
>For example, array A such that:   
    A[0] = 4   
    A[1] = 2   
    A[2] = 2   
    A[3] = 5   
    A[4] = 1   
    A[5] = 5   
    A[6] = 8   
contains the following example slices:    
slice (1, 2), whose average is (2 + 2) / 2 = 2;    
slice (3, 4), whose average is (5 + 1) / 2 = 3;    
slice (1, 4), whose average is (2 + 2 + 5 + 1) / 4 = 2.5.    
The goal is to find the starting position of a slice whose average is minimal.    
the function should return 1, as explained above.    

## 풀이
이중 for문을 돌리면서 평균값을 구하니 timeout 에러가 났다.     
해당문제의 중요한 개념은 a<=b일때 둘의 평균값은 a이상이고 마찬가지로 (a+b)<=(c+d) 일때 두 그룹의 평균값은 a+b이상이다.    
그러니 4로 나누는 경우는 안봐도된다. 2로나눌때 3으로 나눌때의 상황만 보면 된다.    
      
```java
class Solution {
    public int solution(int[] A) {
        float min = (A[0]+A[1])/2f;
        int minIndex = 0;
        
        for(int i=2;i<A.length;i++) {
        	float temp = (A[i-2]+A[i-1]+A[i])/3f;
        	if(min>temp) {
        		min = temp;
        		minIndex = i-2;
        	}
        	
        	temp = (A[i-1]+A[i])/2f;
        	if(min>temp) {
        		min = temp;
        		minIndex = i-1;
        	}
        	
        }
        return minIndex;
    }
}
```