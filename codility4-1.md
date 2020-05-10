# FrogRiverOne
    
> For example, given X = 5 and array A such that:    
  A[0] = 1   
  A[1] = 3   
  A[2] = 1   
  A[3] = 4   
  A[4] = 2   
  A[5] = 3   
  A[6] = 5   
  A[7] = 4   
the function should return 6, as explained above.   
X에 닿기 위해 점프는 한칸씩 할 수 있다. 1 ~ X 까지 값이 있는지 체크하면된다.    
중복값을 허용하지 않기 위해 HashSet을 쓰고 size를 구했다.   
	
## 풀이   
   
```java
import java.util.HashSet;

class Solution {
    public int solution(int X, int[] A) {

        HashSet<Integer> set = new HashSet<Integer>();

        for(int i=0;i<A.length;i++){
            if(A[i] <= X){
                set.add(A[i]);
            }

            if(set.size() == X){
                return i;
            }
        }
        return -1;

    }
}
```