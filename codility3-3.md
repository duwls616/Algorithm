# codility3-3  
>For example, consider array A such that:   
  A[0] = 3   
  A[1] = 1   
  A[2] = 2   
  A[3] = 4   
  A[4] = 3   
We can split this tape in four places:   
P = 1, difference = |3 − 10| = 7   
P = 2, difference = |4 − 9| = 5   
P = 3, difference = |6 − 7| = 1   
P = 4, difference = |10 − 3| = 7    
   
   
총합을 구해놓고 왼쪽부터 배열값을 더하면 총합이 줄어든다. 이 둘의 차이값을 구하면된다.   
-값은 Math.abs함수로 절대값으로 구하고 최솟값은 Math.min을 이용   
```java
public int solution(int[] A) {
	int total = 0;
	int newTotal = 0;
	int min = Integer.MAX_VALUE;
	for(int num : A) {
		total += num;
	}
	
	for(int i=0;i<A.length-1;i++) {
		newTotal += A[i];
		total -= A[i];
		min = Math.min(min, Math.abs(total-newTotal));
	}
	
	return min;
}
```