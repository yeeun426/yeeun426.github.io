---
title: "[Mission] 내가 만든 순열/조합/부분집합 문제"
categories: [Ureca, Algorithm]
tags: [Combination, Permutation]
image:
  path: /assets/post/2025/ureca/combination.png
  alt: java
published: true
---

### 💡 순열 
```혼자 식당에가서 먹을 메뉴를 겹치지 않게 2개 시켜서 먹는 경우의 수 ```
### 💡 조합 
```둘이 식당에가서 각자 먹을 메뉴를 겹치지 않게 각각 하나씩 시켜서 먹는 경우의 수```

```java
package task;
import java.util.Arrays;

// 조합: 30개 메뉴 중 혼자 메뉴 2개를 먹는 경우 (순서 X, 중복 X)
// 순열: 30개 메뉴 중 두 명이 각각 하나씩 메뉴를 선택하는 경우 (순서 O, 중복 X)

public class 식당_순열_조합 {
	static int totalCnt;
    static int[] menu = new int[30]; // 메뉴 30
	static int n; // 고를 메뉴 개수 
	static int[]  results;// 선택된 메뉴
	static boolean[] isSelected;//중복을 피하기 위해 첫 판에서 어떤 수를 뽑았는지 마크해 놓을 배열
	
	public static void main(String[] args) {
        for (int i = 0; i < 30; i++) {
            menu[i] = i + 1;
        }
		n=2; // 메뉴 2
        System.out.println("혼자 식사");
		results = new int[2];
        totalCnt = 0;
        혼자식사(0,0);
		System.out.println("조합 개수:" + totalCnt);
		
        System.out.println("두명 식사");
        results = new int[2];
        isSelected = new boolean[30];
        totalCnt = 0;
        두명식사(0);
        System.out.println("순열 개수:" + totalCnt);

	}
	
	// 혼밥 - 조합(순서 x, 중복 x)
	public static void 혼자식사(int cnt, int start) {
		if(cnt == n) {
			totalCnt++;
			System.out.println(Arrays.toString(results));
			return;
		}
		
		for (int i = start; i < 30; i++) {
            results[cnt] = menu[i];
            혼자식사(cnt + 1, i + 1);
		}
	}
	
    // 두명 식사 (순서O, 중복X)
    public static void 두명식사(int cnt) {
        if (cnt == 2) {
            totalCnt++;
            System.out.println(Arrays.toString(results));
            return;
        }

        for (int i = 0; i < 30; i++) {
            if (isSelected[i]) continue;
            results[cnt] = menu[i];
            isSelected[i] = true;
            두명식사(cnt + 1);
            isSelected[i] = false;
        }
    }
}
```

### 💡 부분집합 : 메뉴 조합

```
김밥, 떡볶이, 튀김, 오뎅, 치즈볼 중에서 식사할 메뉴를 골라서 먹으려 합니다. 
식사할 메뉴를 선택하는 방법은 여러 가지가 있을 수 있습니다. 예를 들어, 한 가지 메뉴만 선택하거나, 두 가지 메뉴를 고를 수도 있습니다.       
또한, 세 가지 메뉴나 네 가지 메뉴를 선택하는 것도 가능합니다. 가능한 모든 메뉴의 조합을 구하세요.
```

```java
package task;

public class 식당_부분집합 {	
	static int totalCnt;
	static String[] menu = {"김밥", "떡볶이", "튀김", "오뎅", "치즈볼"}; // 메뉴 5개
	static boolean[] isSelected;
	
	public static void main(String[] args) {		
		isSelected = new boolean[5];	
		subset(0);	
		System.out.println("총 부분집합의 개수: " + totalCnt);
	}
	
	// 부분집합 생성 함수
	public static void subset(int cnt) {
		// cnt가 5이면 모든 원소를 고려한 상태이므로 부분집합을 하나 완성한 것
		if (cnt == 5) {
			++totalCnt;
			for (int i = 0; i < 5; i++) {
				System.out.print((isSelected[i] ? menu[i] : "X") + " ");
			}
			System.out.println(); 
			return; 
		}
		
		// 현재 메뉴를 선택하는 경우
		isSelected[cnt] = true;
		subset(cnt + 1); // 다음 메뉴로 진행
		
		// 현재 메뉴를 비선택하는 경우
		isSelected[cnt] = false; 
		subset(cnt + 1); // 다음 메뉴로 진행
	}
}
```
