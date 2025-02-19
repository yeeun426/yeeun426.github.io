---
title: "PCCE 기출 JAVA 20문제"
categories: [Ureca, Algorithm]
tags: [java, Algorithm]
image:
  path: /assets/post/2025/ureca/algorithmTeam1.png
  alt: java
published: true
---
### 1. [PCCE 기출문제] 5번 / 산책
```java
class Solution {
    public int[] solution(String route) {
        int east = 0;
        int north = 0;
        int[] answer = new int [2];
        for(int i=0; i<route.length(); i++){
            switch(route.charAt(i)){
                case 'N':
                    north++;
                    break;
                case 'S':
                    north--;
                    break;
                case 'E':
                    east++;
                    break;
                case 'W':
                    east--;
                    break;
            }
        }
        answer[0] = east;
        answer[1] = north;
        return answer;
    }
}
```

### 2. [PCCE 기출문제] 4번 / 저축
```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int start = sc.nextInt();
        int before = sc.nextInt();
        int after = sc.nextInt();

        int money = start;
        int month = 1;
        while (money < 70) {
            money += before;
            month++;
        }
        while (money < 100) {
            money += after;
            month++;
        }
        System.out.println(month);
    }
}
```

### 3. [PCCE 기출문제] 4번 / 병과분류
```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String code = sc.next();
        String lastFourWords = code.substring(code.length()-4, code.length());
        if(lastFourWords.equals("_eye")){
            System.out.println("Ophthalmologyc");
        }
        else if(lastFourWords.equals("head")){
            System.out.println("Neurosurgery");
        }
        else if(lastFourWords.equals("infl")){
            System.out.println("Orthopedics");
        }
        else if(lastFourWords.equals("skin")){
            System.out.println("Dermatology");
        }
        else {
            System.out.println("direct recommendation");
        }
    }
}
```

### 4.[PCCE 기출문제] 2번 / 피타고라스의 정리
```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int a = sc.nextInt();
        int c = sc.nextInt();

        int b_square = c*c - a*a;

        System.out.println(b_square);
    }
}
```

### 5. [PCCE 기출문제] 3번 / 나이 계산
```java
public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int year = sc.nextInt();
        String age_type = sc.next();
        int answer = 0;

        if (age_type.equals("Korea")) {
            answer = 2030 - year + 1;
        }
        else if (age_type.equals("Year")) {
            answer = 2030 -year;
        }
        System.out.println(answer);
    }
}
```

### 6. [PCCE 기출문제] 7번 / 가습기
```java
class Solution {
    public int func1(int humidity, int val_set){
        if(humidity < val_set)
            return 3;
        return 1;
    }

    public int func2(int humidity){
        if(humidity >= 50)
            return 0;
        else if (humidity >= 40)
            return 1;
        else if (humidity >= 30)
            return 2;
        else if (humidity >= 20)
            return 3;
        else if (humidity >= 10)
            return 4;
        else
            return 5;
    }

    public int func3(int humidity, int val_set){
        if(humidity < val_set)
            return 1;
        return 0;
    }

    public int solution(String mode_type, int humidity, int val_set) {
        int answer = 0;

        if(mode_type.equals("auto")){
            answer = func2(humidity);
        }
        else if(mode_type.equals("target")){
            answer = func1(humidity, val_set);
        }
        else if(mode_type.equals("minimum")){
            answer = func3(humidity, val_set);
        }
        return answer;
    }
}

```

### 7. [PCCE 기출문제] 2번 / 각도 합치기
```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int angle1 = sc.nextInt();
        int angle2 = sc.nextInt();

        int sum_angle = angle1 + angle2;
        System.out.println(sum_angle % 360);
    }
}
```

### 8. [PCCE 기출문제] 5번 / 심폐소생술
```java
class Solution {
    public int[] solution(String[] cpr) {
        int[] answer = {0, 0, 0, 0, 0};
        String[] basic_order = {"check", "call", "pressure", "respiration", "repeat"};
        for(int i=0; i< cpr.length; i++){
            for(int j=0; j<basic_order.length; j++){
                if(cpr[i].equals(basic_order[j])){
                    answer[i] = j+1;
                    break;
                }
            }
        }
        return answer;
    }
}
```

### 9. [PCCE 기출문제] 8번 / 닉네임 규칙
```java
class Solution {
    public String solution(String nickname) {
        String answer = "";
        for(int i=0; i<nickname.length(); i++){
            if(nickname.charAt(i) == 'l'){
                answer += "I";
            }
            else if(nickname.charAt(i) == 'w'){
                answer += "vv";
            }
            else if(nickname.charAt(i) == 'W'){
                answer += "VV";
            }
            else if(nickname.charAt(i) == 'O'){
                answer += "0";
            }
            else{
                answer += nickname.charAt(i);
            }
        }
        while(answer.length() < 4){
            answer += "o";
        }
        if(answer.length() > 8){
            answer = answer.substring(0, 8);
        }
        return answer;
    }
}
```

### 10. [PCCE 기출문제] 6번 / 가채점
```java
class Solution {
    public String[] solution(int[] numbers, int[] our_score, int[] score_list) {
        int num_student = numbers.length;
        String[] answer = new String[num_student];

        for (int i = 0; i < num_student; i++) {
            if (our_score[i] == score_list[numbers[i]-1]) {
                answer[i] = "Same";
            }
            else {
                answer[i] = "Different";
            }
        }
        return answer;
    }
}
```

### 11. [PCCE 기출문제] 3번 / 수 나누기
```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int number = sc.nextInt();
        int answer = 0;
        
        for(int i=0; i<=1; i++){
            answer += number % 100;
            number /= 100;
        }

        System.out.println(answer);
    }
}
```

### 12. [PCCE 기출문제] 1번 / 문자 출력
```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        String message = "Let's go!";
        System.out.println("3\n2\n1");
        System.out.println(message);
    }
}
```

### 13. [PCCE 기출문제] 1번 / 출력
```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        String msg = "Spring is beginning";
        int val1 = 3;
        String val2 = "3";

        System.out.println(msg);
        System.out.println(val1 + 10);
        System.out.println(val2 + "10");
    }
}
```

### 14. [PCCE 기출문제] 8번 / 창고 정리
```java
class Solution {
    public String solution(String[] storage, int[] num) {
        int num_item = 0;
        String[] clean_storage = new String[storage.length];
        int[] clean_num = new int[num.length];
        
        for(int i=0; i<storage.length; i++){
            int clean_idx = -1;
            for(int j=0; j<num_item; j++){
                if(storage[i].equals(clean_storage[j])){
                    clean_idx = j;
                    break;
                }
            }
            if(clean_idx == -1){
                clean_storage[num_item] = storage[i];
                clean_num[num_item] = num[i];
                num_item += 1;
            }
            else{
                clean_num[clean_idx] += num[i];
            }
        }
        
        // 아래 코드에는 틀린 부분이 없습니다. 
        int num_max = -1;
        String answer = "";
        for(int i=0; i<num_item; i++){
            if(clean_num[i] > num_max){
                num_max = clean_num[i];
                answer = clean_storage[i];
            }
        }
        return answer;
    }
}
```

### 15. [PCCE 기출문제] 6번 / 물 부족
```java
class Solution {
    public int solution(int storage, int usage, int[] change) {
        int total_usage = 0;
        for(int i=0; i<change.length; i++){
            usage = usage + (usage * change[i] / 100);
            total_usage += usage;
            if(total_usage > storage){
                return i;
            }
        }
        return -1;
    }
}
```

### 16. [PCCE 기출문제] 9번 / 지폐 접기
```java
class Solution {
    public int solution(int[] wallet, int[] bill) {
        int answer = 0;
        
        int wMin = Math.min(wallet[0], wallet[1]);
        int bMin = Math.min(bill[0], bill[1]);
        
        int wMax = Math.max(wallet[0], wallet[1]);
        int bMax = Math.max(bill[0], bill[1]);
        
        while(bMin > wMin || bMax > wMax) {
            if(bill[0] > bill[1]) {
                bill[0] /= 2;                
            } else {
                bill[1] /= 2;             
            }
            bMin = Math.min(bill[0], bill[1]);
            bMax = Math.max(bill[0], bill[1]);
            answer++;
        }
        return answer;
    }
}
```

### 17. [PCCE 기출문제] 7번 / 버스
```java
class Solution {
    public int solution(int seat, String[][] passengers) {
        int num_passenger = 0;
        for(int i=0; i<passengers.length; i++){
            num_passenger += func4(passengers[i]);
            num_passenger -= func3(passengers[i]);
        }
        int answer = func1(seat-num_passenger);
        return answer;
    }

    public int func1(int num){
        if(0 > num){
            return 0;
        }
        else{
            return num;
        }
    }
    public int func2(int num){
        if(num > 0){
            return 0;
        }
        else{
            return num;
        }
    }

    public int func3(String[] station){
        int num = 0;
        for(int i=0; i<station.length; i++){
            if(station[i].equals("Off")){
                num += 1;
            }
        }
        return num;
    }

    public int func4(String[] station){
        int num = 0;
        for(int i=0; i<station.length; i++){
            if(station[i].equals("On")){
                num += 1;
            }
        }
        return num;
    }
}

```

### 18. [PCCE 기출문제] 9번 / 이웃한 칸
```java
class Solution {
    public int solution(String[][] board, int h, int w) {
        int answer = 0;
        int n = board.length;
        int count = 0;
        int[] dh = {0, 1, -1, 0}, dw = {1, 0, 0, -1};
        
        for(int i = 0; i <= 3; i++) {
            int h_check = h + dh[i];
            int w_check = w + dw[i];
            
            if(h_check >= 0 && h_check < n && w_check >= 0 && w_check < n) {
                if(board[h][w].equals(board[h_check][w_check])) {
                    count++;
                }
            }
        }
        return count;
    }
}
```

### 19. [PCCE 기출문제] 10번 / 데이터 분석
```java
import java.util.*;

class Solution {
    
    public int[][] solution(int[][] data, String ext, int val_ext, String sort_by) {
        int[][] answer = {};
        
        Map<String, Integer> map = new HashMap<>();
        map.put("code", 0);
        map.put("date", 1);
        map.put("maximum", 2);
        map.put("remain", 3);
        
        int[][] arr = Arrays.stream(data).filter(t -> t[map.get(ext)] < val_ext).toArray(int[][]::new);
        
        Arrays.sort(arr, (o1, o2) -> {
            return o1[map.get(sort_by)] - o2[map.get(sort_by)];
        });
        return arr;
    }
}
```

### 20. [PCCE 기출문제] 10번 / 공원
> 이 문제는 너무 어려워서 다같이 답을 이해하고 처음부터 다시 풀어보았다. 
> 그래도 같이 처음부터 풀면서 문제를 더 잘 이해할 수 있었다 !

```java
import java.util.*;

class Solution {
    static String[][] park;
    
    static boolean check(int x, int y, int m) {
        for(int i = 0; i < m; i++) {
            for(int j = 0; j < m; j++) {
                if(x + i >= park.length || y + j >= park[0].length) {
                    return false;
                }
                if(!park[x+i][y+j].equals("-1")) return false;
            }
        }
        return true;
    }
    
    public int solution(int[] mats, String[][] inputPark) {
        park = inputPark;
        int maxSize = -1;
        Arrays.sort(mats);
        
        for(int i = 0; i < park.length; i++){
            for(int j = 0; j < park[i].length; j++) {
                if(park[i][j].equals("-1")) {
                    // 매트 사이즈를 돌면서 가능한 지 체크
                    for(int m:mats) {
                        if(check(i, j, m)) {
                            maxSize = Math.max(m, maxSize);
                        } 
                    }
                }
            }
        }
        return maxSize;
    }
}
```

---

## END