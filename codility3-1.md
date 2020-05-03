# FrogJmp
> For example, given:   
  X = 10   
  Y = 85   
  D = 30   
the function should return 3   
   
   
```java
public int solution(int X, int Y, int D) {
        Y = Y-X;
        int count = Y/D;
        if(Y%D>0)
            count += 1;
            
        return count;
    }
```	
   
* while문이나 for문을 쓰면 시간초과가 나왔다.