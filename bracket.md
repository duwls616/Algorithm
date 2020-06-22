# bracket
> A string S consisting of N characters is considered to be properly nested if any of the following conditions is true:   
S is empty;   
S has the form "(U)" or "[U]" or "{U}" where U is a properly nested string;    
S has the form "VW" where V and W are properly nested strings.     
For example, the string "{[()()]}" is properly nested but "([)()]" is not.    
Write a function:      
class Solution { public int solution(String S); }     
that, given a string S consisting of N characters, returns 1 if S is properly nested and 0 otherwise.     
     
```java
import java.util.Stack;

class Solution {
    public int solution(String S) {
		//stack push 텍스트
        String text ="{[(";
		//stack pop 텍스트
		String text2 ="}])";
		
		Stack stack = new Stack();
		for(int i=0;i<S.length();i++) {
			char temp = S.charAt(i);
			if(text.indexOf(temp)>-1)
				stack.push(text.indexOf(temp));
			else if(text2.indexOf(temp) >-1) {
			    if(stack.isEmpty())
			        return 0;
				if((int)stack.peek() == text2.indexOf(temp)) {
					stack.pop();
				}
			}
		}
		
		if(stack.isEmpty())
			return 1;
		else
			return 0;
    }
}
```