# CodeUp1920 2진수 변환
> 어떤 10진수 n이 주어지면 2진수로 변환해서 출력하시오.   
예)     
10    ----->  1010   
0    ----->  0   
1    ----->  1   
2    ----->  10   
1024    ----->  10000000000   
7 -----> 111   

    
## 재귀를 이용
나눗셈을 하는데 나머지값을 역순으로 출력한다.
```java
public class codeTest {
    
    public static void main(String args[]){
        Scanner sc = new Scanner(System.in);
        int input = sc.nextInt();
        calculate(input);
    }
    
    static void calculate(int n){
        if(n==0) {
        	return ;
        }else {
        	calculate(n/2);
        	System.out.print(n%2);
        }
    }
}
```