# Triangle
   
> An array A consisting of N integers is given. A triplet (P, Q, R) is triangular if 0 ≤ P < Q < R < N and:   
A[P] + A[Q] > A[R],   
A[Q] + A[R] > A[P],   
A[R] + A[P] > A[Q].   
For example, consider array A such that:   
   
  A[0] = 10    A[1] = 2    A[2] = 5
  A[3] = 1     A[4] = 8    A[5] = 20      
Triplet (0, 2, 4) is triangular.        
the function should return 1, as explained above. Given array A such that:     
       
  A[0] = 10    A[1] = 50    A[2] = 5
  A[3] = 1    
the function should return 0.     
      
## 풀이
중복되지 않는 인접한 값 3개를 고르고 두개를 더한값이 나머지 한개보다 크면 1을 리턴, 그렇지 않으면 0을 리턴한다.   
즉, A[P] < A[Q] < A[R] 이라면 A[P]+A[Q]>A[R] 인지만 구하면 된다.    
     
```java
import java.util.Arrays;

class Solution {
    public int solution(int[] A) {
        Arrays.sort(A);
        
        for(int i=0;i<A.length-2;i++){
            if(A[i]>A[i+2]-A[i+1]){
                return 1;
            }
        }
        
        return 0;
    }
}
```