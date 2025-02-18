---
title: "[Day17] 순열/조합 문제"
categories: [Ureca, Algorithm]
tags: [Combination, Permutation]
published: true
---

### 문제 만들어보기 (조합 / 순열)

#### 💡 순열 : 혼자 식당에가서 먹을 메뉴를 겹치지 않게 2개 시켜서 먹는 경우의 수 
#### 💡 조합 : 둘이 식당에가서 각자 먹을 메뉴를 겹치지 않게 각각 하나씩 시켜서 먹는 경우의 수


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
		System.out.println("순열 개수:" + totalCnt);
		
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