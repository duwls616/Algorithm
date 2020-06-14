# NumberOfDiscIntersections
     
    	
     
![screenshot3](/img/numberOfDisk.png)   
    
>The figure below shows discs drawn for N = 6 and A as follows:   
  A[0] = 1     
  A[1] = 5    
  A[2] = 2    
  A[3] = 1    
  A[4] = 4    
  A[5] = 0    
     
> There are eleven (unordered) pairs of discs that intersect, namely:    
discs 1 and 4 intersect, and both intersect with all the other discs;    
disc 2 also intersects with discs 0 and 3.     
     
>N is an integer within the range [0..100,000];     
each element of array A is an integer within the range [0..2,147,483,647].     
       
          
## 풀이
현재의 point를 중심으로 시작점(lower)과 끝점(upper)를 구하여 각각의 배열에 저장한다.   
upper 보다 작은 lower 들은 반드시 가장 작은 upper 보다 큰 반지름을 갖는다.        
다음 upper 에서 겹치지 않게 현재 J 만큼 빼준다.   
A의 범위는 0~2,147,483,647이니 배열은 long으로 해준다.    
   
```java
import java.util.Arrays;

class Solution {
    public int solution(int[] A) {
        long[] upper = new long[A.length];
        long[] lower = new long[A.length];
        
        for(int i=0;i<A.length;i++){
            upper[i] = (long)i+A[i];
            lower[i] = (long)i-A[i];
        }
        
        Arrays.sort(upper);
        Arrays.sort(lower);
        
        int interaction = 0;
        int j = 0;
        for(int i=0;i<A.length;i++){
            while(j<A.length && upper[i] >= lower[j]){
                interaction += j;
                interaction -= i;
                j++;
            }
        }
        
        if(interaction > 10000000){
            return -1;
        }
        
        return interaction;
    }
}
```   