# max counter
> 입력 :  int배열 A와 int N   
	A[0] = 3    
    A[1] = 4    
    A[2] = 4       
    A[3] = 6       
    A[4] = 1    
    A[5] = 4    
    A[6] = 4    
  출력 : [3, 2, 2, 4, 2]    
  조건 : A[K]=X 이면 새 배열의 X-1번째 데이터가 1씩 증가한다.    
  A[K]=N+1 이면 새 배열의 모든 데이터가 max값으로 셋팅된다.    
       
## 풀이1
```java
class Solution {
    public int[] solution(int N, int[] A) {
        int lastMax = 0;
        int currentMax = 0;
        int[] arr = new int[N];
        for(int i=0;i<A.length;i++){
            if(lastMax<currentMax)
                lastMax = currentMax;
            
            if(A[i]>N){
                for(int j=0;j<N;j++){
                    arr[j] = lastMax;
                }
            }else{
                arr[A[i]-1] += 1;
                if(arr[A[i]-1]>currentMax)
                    currentMax = arr[A[i]-1];
            }
                
        }
        
        return arr;
    }
}
```
* 시간초과가 나왔다.......A[K]=N+1일 때마다 max값을 셋팅해서 시간초과가 나왔다. 맨 마지막에만 max를 더해줘야한다고 한다.

	 
## 풀이2
```java	 
class Solution {
    public int[] solution(int N, int[] A) {
        int lastMax = 0;
        int currentMax = 0;
        int[] arr = new int[N];
        
        for(int i=0;i<A.length;i++){
            
            
            if(A[i]>N){
                if(lastMax < currentMax)
                    lastMax = currentMax;
            }else{
                if(arr[A[i]-1]<lastMax)
                    arr[A[i]-1] = lastMax;
                    
                arr[A[i]-1]++;
                
                if(arr[A[i]-1]>currentMax)
                    currentMax = arr[A[i]-1];
            }
                
        }
        
        for(int i=0;i<N;i++){
            if(arr[i] < lastMax){
                arr[i] = lastMax;    
            }
        }
        
        return arr;
    }
}	  
```