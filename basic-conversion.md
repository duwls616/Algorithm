# 변환   

## 진수변환
1. 10진수 -> 2진수   
Integer.toBinaryString(int value)   
  
2. 10진수 -> 8진수  
Integer.toOctalString(int value)  
  
3. 10진수 -> 16진수   
Integer.toHexString(int value)  

4. 2진수 -> 10진수  
Integer.valueOf(string, 2)  
  
5. 8진수 -> 10진수  
Integer.valueOf(string, 8)  

6. 16진수 -> 10진수  
Integer.valueOf(string, 10)  
  
## 대문자 <-> 소문자  
1. 내장함수 사용  
``` 
Scanner sc = new Scanner(System.in);
String str = sc.nextLine();  

String upper = str.toUpperCase();  
String lower = str.toLowerCase();  
```  

2. ASCII 코드값 차이를 이용  
:대문자와 소문자의 차이는 32! 대문자로 변환할땐 -32, 소문자로 변환할땐 +32
```
Scanner sc = new Scanner(System.in);
String str = sc.nextInt();

char[] arr;
arr = str.toCharArray();

for(int i=0;i<arr.length;i++){
	arr[i] = (char)(arr[i]-32);
}
```

## String.format  
String.format(%[argument_index$][flags][width]conversion)  
  
1. argument_index$  
: 들어갈 파라미터의 인덱스, 1부터 시작  
  
```
// B A출력
System.out.printlnn(String.format("%2$10s%1$10s","A","B"))  
```  

2. flags 옵션  
: '-'를 넣으면 문자열이 왼쪽 정렬된다.  

3. width옵션  
: 문자열의 길이  

4. conversion(필수값)

* %d : 10진수  
* %x : 16진수   
* %o : 8진수  
* %f : 실수   

```
// 123, 678
System.out.printlnn(String.format("%d, %d",123, 678));  
// 678, 123
System.out.printlnn(String.format("%2$d, %1$d",123, 678));  
//123 678
System.out.printlnn(String.format("%-10d %-10d",123, 678));  

// 0flag로 공백채우기,  정수나 실수에 사용가능  
// 0000000123, 0000000789
System.out.printlnn(String.format("%010d, %010d",123, 678)); 

// ',' flag 사용  
// 해당국가에서 사용하는 기호로 숫자를 그룹지어 준다.  
System.out.printlnn(String.format("%,10d%,10d",10000, -20000));   
```

