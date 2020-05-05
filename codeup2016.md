# codeup2016 stack
> 첫째 줄에 숫자의 길이 n이 입력된다. (1 <= n <= 200)   
둘째 줄에 길이가 n인 숫자가 입력된다.   
입력예시   
8   
12421421   
출력예시   
12,421,421   
   
## stack을 이용한 문제풀이
stack의 포인터가 3의 배수인지 확인하면서 배수이면 ,출력
   
```java
import java.util.Scanner;

public class Main{
    public static void main(String args[]){
        Scanner sc= new Scanner(System.in);
        int size = Integer.parseInt(sc.nextLine());
        String text = sc.nextLine();
        char[] arr = text.toCharArray();
        int ptr = size-1; //stack의 포인터
        
        String temp = "";
        for(int i=0;i<size;i++){
        	temp+=arr[i];
        	if(ptr%3 == 0 && ptr!=0){
        		temp += ",";
        	}
        	ptr--;
        }
        
        System.out.println(temp);
    }
}
```