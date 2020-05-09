# codeup2605
> 캔디팡 격자판(7 * 7)의 색깔 정보(1~5)가 입력된다.   
※ 색깔정보   
빨강 = 1 , 노랑 = 2 , 파랑 = 3 , 초록 = 4 , 보라 = 5
	
## 입력
> 2 1 5 1 1 3 4   
2 1 5 1 3 5 3   
2 3 4 5 2 2 4   
4 4 3 2 3 1 3   
4 3 5 3 1 4 3   
5 4 4 3 3 5 5	
2 1 3 5 1 1 2	
	
## 출력
4
		
## 풀이
재귀와 2차원배열을 이용해서 풀었다. 연결된 상하좌우 item의 값을 체크하고       
방문한 곳을 중복으로 체크하지않기 위해 visit 배열을 따로 만들었다.
```java
public class dfsArray2 {
	static int[][] arr;	//입력받은 영역
	static int[][] visit;	//방문한 영역
	static int count = 0;
	static int total = 0;
	public static void main(String[] args) {
		arr = new int[7][7];
		visit = new int[7][7];
		
		Scanner sc = new Scanner(System.in);
		
		for(int i=0;i<arr.length;i++) {
			for(int j=0;j<arr.length;j++) {
				arr[i][j] = sc.nextInt();
			}
		}
		
		for(int i=0;i<arr.length;i++) {
			for(int j=0;j<arr.length;j++) {
				dfs(i, j, arr[i][j]);
				if(count >= 3) {
					total ++;
				}
				count = 0;
			}
		}
		
		System.out.println(total);
		
	}
	
	public static void dfs(int x, int y, int number) {
		if(x >= 0 && y>= 0 && x < 7 && y < 7) {
			if(number==arr[x][y] && visit[x][y]!=1) {
				count ++;
				visit[x][y] = 1;
				dfs(x-1,y,number);
				dfs(x,y-1,number);
				dfs(x+1,y,number);
				dfs(x,y+1,number);
			}
		}
	}
}
```