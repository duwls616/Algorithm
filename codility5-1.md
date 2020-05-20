# CountDiv
> given three integers A, B and K, returns the number of integers within the range [A..B] that are divisible by K, i.e.:   
>   
>{ i : A ≤ i ≤ B, i mod K = 0 }    
>     
>For example, for A = 6, B = 11 and K = 2, your function should return 3, because there are three numbers divisible by 2 within the range [6..11], namely 6, 8 and 10.   

## 풀이
A가 K로 나눠떨어질때마다 K를 더해가면서 count값을 증가시켰더니 시간초과가 나왔다.    
나눠떨어질때 K로 나눈값을 count에 더하는 로직으로 수정하였더니 복잡도가 O(1)가 나왔다.    
```java
class Solution { 
	public int solution(int A, int B, int K){
		int count = 0;
		int num = A;
		while(num<=B){
			if(num%K==0){
				count++
				count += (B-num)/K;
				break;
			}else
				num++;
		}
		return count;
	}	
}
```