## Greedy

- 현재 상황에서 지금 당장 좋은 것만 고르는 방법
- 문제를 풀기 위한 최소한의 아이디어를 떠올릴 수 있는 능력 요구
- 정당성 분석이 중요함
   - 단순히 좋아 보이는 것을 반복적으로 선택해도 최적의 해를 구할 수 있는지 검토해야함

그리디 알고리즘은 언제나 해답을 주어지지 않는다. 트리로 예를 들어보면
<br><br>
노드를 거쳐 합을 구했을때가장 큰 값을 구하면 이렇게 될것이다. 결과 : 21<br><br>  
<div align = "center">

![그리디1](https://user-images.githubusercontent.com/86589565/132270714-ceec3ee9-8aa4-4583-a7bc-6af1bb82b9d5.png)

</div>
<br>
하지만 여기서 Greedy 알고리즘을 적용한다면 가장 현재값 중 가장 큰 값으로만 찾아 가서 결과는 19가 된다.<br><br> 

<div align = "center">

![그리디2](https://user-images.githubusercontent.com/86589565/132270717-73500531-15f9-49ef-b1d4-3b832944422d.png)


</div>

그리디의 대표적인 알고리즘 문제는 거스름돈에 있다. 손님이 만약
2260원을 거스름돈을 받는다 라고 가정한다 <br>(단 여기서 거스름돈을 돈전으로만 받고 거스름받는돈 N은 10의 배수이다)<br>

머리속으로 생각해 봤을땐 500원 동전 4개 나머지 100원 동전 2개 50원 동전 1개 10원 동전 1개를 주었을떄가 가장 최소한의 해를 구하는것이 될 것이다.

하지만 만약 거스름 받는돈이 800원이고 동전 종류로 500원 400원 100원이 존재한다면 500원 1개와 100원 3개보다 400원 동전 2개가 해답이 된다. 즉, 다시 말하지만 그리드는 항상 해답을 주어지는것이 아니다.<br>

N이 1이 될떄까지 ?

Python
```python
n,k = map(int,input(), split()) ## 공백을 인지하여 입력 받기
result = 0

while n != 1:
  if ((n % k) == 0):
    n = n / k
    result +=1
  else:
    n -=1
    result+=1

print(result)

```
<br>
Java

```java
import java.util.Scanner;
public class Greedy {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		int n = sc.nextInt();
		int k = sc.nextInt();
		int result = 0;
		while (n != 1) {
			if ((n % k) ==0) {
				n = n / k;
				result += 1;
			}
			else {
				n -=1;
				result +=1;
			}
		}
		System.out.println("정답은 :"+result );
	}		
}
```

문자열이 주어졌을때 가장 큰값
```python
n = input()
result=0
for i in n:
     if(int(i) == 0 or int(i) == 1 ):
       result += int(i)
     else:
       if (result != 0):
         result *= int(i)
       else:
          result += int(i)
print(result)
```

Java
```java
//먼저 문자열을 정수형으로 바꾸는 함수 integer.parseInt(문자열), 정수형을 문자열로 바꾼느 함수 integer.toString(정수형)
//또한 파이썬 처럼 for문을 똑같이 구현하는건 힘들기에 문자열.charAt(순번쨰)로 해야함 (이작업은 문자열을 아스키코드로 변환시키는 작업)그리고 그 문자열을 더할때 '0'을 뺴줘야댐 

public class Greedy2 {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		String str = sc.next();
		int result = 0;
		
		for (int i =0; i < str.length() ; i++) {
			if (str.charAt(i) == 1 || str.charAt(i) == 0) {
			   result +=  str.charAt(i)-'0';
			}else {
				if (result == 0) {
					result +=str.charAt(i) -'0';
				}else {
					result *=str.charAt(i)-'0';
				}
			}
		}
		System.out.println(result);
		
	}
}

```


[출처 동빈나 유투브](https://www.youtube.com/watch?v=2zjoKjt97vQ)