# CodeUp 1916
> 피보나치 수열이란 앞의 두 수를 더하여 나오는 수열이다.   
첫 번째 수와 두 번째 수는 모두 1이고, 세 번째 수부터는 이전의 두 수를 더하여 나타낸다. 피보나치 수열을 나열해 보면 다음과 같다.   
1,1,2,3,5,8,13…    
자연수 N을 입력받아 N번째 피보나치 수를 출력하는 프로그램을 작성하시오.    
단, N이 커질 수 있으므로 출력값에 10,009를 나눈 나머지를 출력한다.
     
	 
## 동적계획법(Dynamic Programming, DP)   
큰 문제를 작은문제로 나눠서 푼다.
    
	  
### 하향식 기법을 이용한 알고리즘
      
```java
public class CodeTest {
static int[] arr;
    
    public static void main(String args[]){
        Scanner sc = new Scanner(System.in);
        int input = sc.nextInt();
        arr = new int[input+1];
        int total = dp(input);
        System.out.println(total);
    }
    
    static int dp(int n){
        if(n == 1 || n == 2){
            return 1;
        }
        if(arr[n]!=0) return arr[n];
        
        arr[n] = (dp(n-1)+dp(n-2))%10009;
        return arr[n];
    }
}
```   
   
   
### 상향식 기법을 이용한 알고리즘
   
```java
public class CodeTest {
static int[] arr;
    
    public static void main(String args[]){
        Scanner sc = new Scanner(System.in);
        int input = sc.nextInt();
        arr = new int[input+1];
        int total = dp(input);
        System.out.println(total);
    }
    
    static int dp(int n){
        arr[0]=0;
		arr[1]=1;
		for(int i=2;i<=n;i++){
			arr[i] = arr[i-1] + arr[i-2];
		}
		
		return arr[n];
    }
}
```   