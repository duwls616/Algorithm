# codility lesson 1
> For example, given N = 1041 the function should return 5, because N has binary representation 10000010001 and so its longest binary gap is of length 5. Given N = 32 the function should return 0, because N has binary representation '100000' and thus no binary gaps.
    
    
Integer 클래스의 toBinaryString으로 2진수 변환을 해준 후 0이 나온 경우 count, 1이면 max값에 count 값을 넣어주었다.
   
```java

public int solution(int n){
	int count = 0;
	int max = 0;
	String binaryStr = Integer.toBinaryString(n);
	
	for(int i=0;i<binaryStr.length();i++){
		char temp = binaryStr.charAt(i);
		if(temp == '0'){
			count++;
		}else{
			max = (count > max)? count: max;
			count = 0;
		}
	}
	
	return max;
}

   