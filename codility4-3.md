# MissingInteger
> 입력:    
A = [1, 3, 6, 4, 1, 2]     
출력:      
5      	
int 배열에 포함되지않는 제일 작은 양수를 찾는다.   		
			
			
## 풀이
```java
import java.util.Arrays;

class Solution {
    public int solution(int[] A) {
       int min = 1;
       Arrays.sort(A);
       
       for(int item: A){
           if(item == min)
                min++;
       }
       
       return min;
    }
}
```			
* 오름차순 정렬 후 제일작은 min값을 구해간다. 복잡도는 O(N) or O(N * log(N))가 나왔다.