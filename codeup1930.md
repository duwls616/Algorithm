# codeUp1930
>  SuperSum  함수는 다음과 같이 정의된다.       
SuperSum(0,n)=n (n은  모든 양의 정수)       
SuperSum(k,n)=SuperSum(k−1,1)+SuperSum(k−1,2)+...+SuperSum(k−1,n)       
k와 n이 여러개 주어진다. SuperSum의 값을 각각 출력하시오.         
          
입력     
1 3   
2 3    
4 10    
10 10    
출력    
6    
10    
2002    
167960    

## 풀이
:재귀 문제 중 메모이제이션 기법을 사용하는 문제이다.    
이미 계산했던 값이라면 배열에서 값을 꺼내고 그렇지 않다면 superSum(k,n) = superSum(k-1, 1)+...+superSum(k-1,n) 이므로 for문을 돌려 배열에 저장한다.    
마지막엔 for문으로 얻어낸 값을 리턴한다.    
      
```java
import java.util.Scanner;

public class Main{
    static int[][] arr = new int[15][15];
    public static void main(String args[]){
        Scanner sc = new Scanner(System.in);
        
        //입력시 갯수를 모를 때
        while(sc.hasNextInt()) {
        	int k = sc.nextInt();
            int n = sc.nextInt();
            int temp = superSum(k,n);
            System.out.println(temp);
        }
        
    }
    
    static int superSum(int k, int n){
    	//메모이제이션 기법(이미 계산했던 값이라면 배열의 값 return)
    	if(arr[k][n]>0) {
    		return arr[k][n];
    	}else if(k==0) {
    		return n;
    	}else {
    		for(int i=1;i<n+1;i++) {
    			arr[k][n]+=superSum(k-1,i);
    		}
    	}
    	
    	return arr[k][n];
    }
}
```
