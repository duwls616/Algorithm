# codility lesson2 OddOccurencesInArray
>> For example, given array A such that:  
  A[0] = 9  A[1] = 3  A[2] = 9  
  A[3] = 3  A[4] = 9  A[5] = 7  
  A[6] = 9  
the function should return 7  
짝이 없는 7을 return 해줘야 한다.   
   
## XOR 연산
이 문제를 풀기위해선 XOR연산에 대해 알아볼 필요가 있다.   
비트연산을 할때 1이 홀수개이면 1, 짝수개이면 0을 리턴해준다.   
예를 들어 1^1 =0,   
1^1^1 = 1,   
1010^1010 = 0000,   
1010^1010^1010 = 1010   
자기자신과 짝수번 연산하면 0이되고, 홀수번 연산하면 자기자신이 된다.   
   
   
```java
public int solution(int[] A){
	int answer = 0;
	for(int i=0;i<A.length;i++){
		answer = answer ^ A[i];
	}
	return answer;
}	
```
   
* 1001, 0011, 1001, 0011, 1001, 0111, 1001을 비트연산하면 짝이없는 7(0111)만 남는다.
* 참고로 비트단위 연산자는 ~(bitwise not), &(bitwise and), |(bitwise or), ^(bitwise xor), <<(bitwise left shift), >>(bitwise right shift)