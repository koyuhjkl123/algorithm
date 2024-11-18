# 알고리즘 문제 풀이
알고리즘 문제를 보고 나의 풀이 설명과 푸는 코드와 방식을 설명




## 01_문제
### 문제명 : 알람 시계 <br>
상근이는 매일 아침 알람을 듣고 일어난다. 알람을 듣고 바로 일어나면 다행이겠지만, 항상 조금만 더 자려는 마음 때문에 매일 학교를 지각하고 있다. <br>
상근이는 모든 방법을 동원해보았지만, 조금만 더 자려는 마음은 그 어떤 것도 없앨 수가 없었다. <br>
이런 상근이를 불쌍하게 보던 창영이는 자신이 사용하는 방법을 추천해 주었다. <br>
바로 "45분 일찍 알람 설정하기"이다. <br>
이 방법은 단순하다. 원래 설정되어 있는 알람을 45분 앞서는 시간으로 바꾸는 것이다. 어차피 알람 소리를 들으면, 알람을 끄고 조금 더 잘 것이기 때문이다. 이 방법을 사용하면, 매일 아침 더 잤다는 기분을 느낄 수 있고, 학교도 지각하지 않게 된다. <br>
현재 상근이가 설정한 알람 시각이 주어졌을 때, 창영이의 방법을 사용한다면, 이를 언제로 고쳐야 하는지 구하는 프로그램을 작성하시오. <br>


### 예시 설명
입력 : h = 10, m = 10 <br>
출력 : h = 9,  m = 25 <br>

<br>
입력 : h = 0, m = 30 <br>
출력 : h = 23, m = 45 <br>

### 풀이 설명
입력받은 분이 -45분을뺀 후 0보다 작으면 시(hour)-1 하고 분(minute) 60를 더해주고, 아닐경우 45분을 빼주면 된다.
아울러 시(hour)가 0보다 작을 경우 23시로 변경하면 된다.

### 풀이 코드

```
import java.util.Scanner;

public class Main {

	public static void main(String[] args) {
		
		Scanner sc = new Scanner(System.in);
		
		int h = sc.nextInt(); // 시간 입력
		int m = sc.nextInt(); // 분 입력
		
		m -= 45;

    // m - 45 = 음수라면 h-1, m +=60
		if(m <0) {
			
			h--;
			m += 60;
			// 시간이 음수라면 23로 변경
			if(h <0) {
				h = 23;
			}
		}
		// 최종 결과 출력
		System.out.println(h);
		System.out.println(m);
		
	}
	
}

```

## 02_문제
### 문제명 : 오븐 시계 <br>
KOI 전자에서는 건강에 좋고 맛있는 훈제오리구이 요리를 간편하게 만드는 인공지능 오븐을 개발하려고 한다. <br>
인공지능 오븐을 사용하는 방법은 적당한 양의 오리 훈제 재료를 인공지능 오븐에 넣으면 된다. 그러면 인공지능 오븐은 오븐구이가 끝나는 시간을 분 단위로 자동적으로 계산한다. <br>
또한, KOI 전자의 인공지능 오븐 앞면에는 사용자에게 훈제오리구이 요리가 끝나는 시각을 알려 주는 디지털 시계가 있다. <br>
훈제오리구이를 시작하는 시각과 오븐구이를 하는 데 필요한 시간이 분단위로 주어졌을 때, 오븐구이가 끝나는 시각을 계산하는 프로그램을 작성하시오. <br>

### 예시 설명
입력 : h = 14, m = 30, mm = 20 <br>
출력 : h = 14, m = 50 <br>

<br>

입력 : h = 17, m = 40, mm = 80 <br>
출력 : h = 19, m = 0 <br>


### 풀이 설명
(입력 받은 분 + 필요시간 분) >= 60이라면, 1시간을 추가하고, 23시에서 1시간을 추가할 경우 0을 한다.


### 풀이 코드
```
import java.util.Scanner;

public class Main {

	public static void main(String[] args) {
		
		
		Scanner sc = new Scanner(System.in);
		
		int h = sc.nextInt();
		int m = sc.nextInt();
		int mm = sc.nextInt();
		
		m = m + mm;
		
		if(m >= 60) {
			
			h += m / 60;
            m %= 60;
			
			if(h >= 24) {
				h %= 24;
			}
			
		}
		System.out.print(h+ " " +m);
		
		
	}
	

}

```

## 3_문제
### 문제명 : 주사위 세개
1에서부터 6까지의 눈을 가진 3개의 주사위를 던져서 다음과 같은 규칙에 따라 상금을 받는 게임이 있다. <br> 
같은 눈이 3개가 나오면 10,000원+(같은 눈)×1,000원의 상금을 받게 된다. <br>
같은 눈이 2개만 나오는 경우에는 1,000원+(같은 눈)×100원의 상금을 받게 된다. <br>
모두 다른 눈이 나오는 경우에는 (그 중 가장 큰 눈)×100원의 상금을 받게 된다. <br>
예를 들어, 3개의 눈 3, 3, 6이 주어지면 상금은 1,000+3×100으로 계산되어 1,300원을 받게 된다. 또 3개의 눈이 2, 2, 2로 주어지면 10,000+2×1,000 으로 계산되어 12,000원을 받게 된다. <br>
3개의 눈이 6, 2, 5로 주어지면 그중 가장 큰 값이 6이므로 6×100으로 계산되어 600원을 상금으로 받게 된다. <br>
3개 주사위의 나온 눈이 주어질 때, 상금을 계산하는 프로그램을 작성 하시오. <br>

### 예시 설명
입력 : a = 3, b = 3, c = 6 <br>
출력 : 1300 <br>

<br>

입력 : a = 2, b = 2, c = 2 <br>
출력 : 12000 <br>

### 풀이 설명


### 풀이 코드
```
```
