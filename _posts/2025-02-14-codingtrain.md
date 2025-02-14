---
title: "[Day14] JAVA 알고리즘 기초 30문제"
categories: [Ureca, Algorithm]
tags: [java, Algorithm]
image:
  path: /assets/post/2025/ureca/algorithm70.png
  alt: java
published: true
---

오늘 자바 수업과 총 70문제의 자바 기초 문제를 풀면서 한 생각은 여러 메서드들이 많아서
자바스크립트에 비해서 편리하다는 거였습니다.<br/>
예전에 알고리즘 스터디를 했을 당시 자바로 풀던 친구가 자바에는 메서드로 있는데 js에서는 다 구현해야 된다고 설명해줬던게 무슨 뜻인지 알거같아서 자바로 풀면 이런게 편할 수 있겠다 ! 싶어서 조금 더 공부해보고 싶습니다 :)

---

---

### 1. 수 조작하기 1
```java
class Solution {
    public int solution(int n, String control) {
        String [] controlArr = control.split("");
        
        for(int i = 0 ; i < controlArr.length ; i++) {
            switch(controlArr[i]) {
                case "w" :
                    n += 1;
                    break;
                case "s" :
                    n -= 1;
                    break;
                case "d" :
                    n += 10;
                    break;
                case "a" :
                    n -= 10;
                    break;
            }
        }
        return n;
    }
}
```

### 2. 마지막 두 원소
```java
class Solution {
    public int[] solution(int[] num_list) {
        int[] answer = new int[num_list.length + 1];

        for(int i = 0 ; i< num_list.length ; i++) {
            answer[i] = num_list[i];
        }
        if(num_list[num_list.length-1] > num_list[num_list.length-2]) {
            answer[num_list.length] = num_list[num_list.length-1] - num_list[num_list.length-2];
        } else {
            answer[num_list.length] = num_list[num_list.length-1] * 2;
        }       
        return answer;
    }
}
```

### 3. 원소들의 곱과 합
```java
class Solution {
    public int solution(int[] num_list) {
        int a = 1;
        int b = 0;
       for(int c:num_list){
           a *=c;
           b +=c;
       }
        if(a < b*b){
            return 1;
        }else{
            return 0;
        }
    }
}
```

### 4. 문자 리스트를 문자열로 변환하기
```java
class Solution {
    public String solution(String[] arr) {
        return String.join("", arr);
    }
}
```

### 5. 문자열 돌리기
```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String a = sc.next();
        
        for(String str:a.split("")){
           System.out.println(str);
        }
    }
}
```

### 6. I로 만들기
```java
/* 아스키 코드 */
/* toCharArray 문자열을 char Array로*/
class Solution {
    public String solution(String myString) {
        char ch = 'l';
        int num = (int)ch;
        String answer="";
        for(char str:myString.toCharArray()){
            int numStr=(int)str;
            if(numStr>num){
                answer+=str;
            }else{
                answer+=ch;
            }  
        }
        return answer;
    }
}
```

### 7. 특별한 이차원 배열 1
```java
class Solution {
    public int[][] solution(int n) {
       int[][] arr=new int[n][n];
        
        for(int i=0;i<n;i++){
            arr[i][i]=1;
        }
        return arr;
    }
}
```

### 8. 간단한 식 계산하기
```java
class Solution {
    public int solution(String binomial) {
        String[] str= binomial.split(" ");
        int a=Integer.parseInt(str[0]);
       
        int b=Integer.parseInt(str[2]);
        
        switch(str[1]){
            case "+": return a+b;
            case "-": return a-b;
            case "*": return a*b;  
            default: return 0;
        }
    }
}
```

### 9. 주사위 게임1
```java
class Solution {
    public int solution(int a, int b) {
        int answer = 0;
        
        if(a % 2 != 0 && b % 2 != 0) {
            return a*a + b*b;
        } else if (a % 2 == 0 && b % 2 == 0) {
            return Math.abs(a-b);
        } else {
            return 2 * (a+b);
        }
    }
}
```

### 10. 조건에 맞게 수열 변환하기 3
```java
class Solution {
    public int[] solution(int[] arr, int k) {
        if(k % 2 != 0) {
            for(int i = 0 ; i < arr.length ; i++) {
                arr[i] *= k;
            }
        } else {
            for(int i = 0 ; i < arr.length ; i++) {
                arr[i] += k;
            }
        }

        return arr;
    }
}
```

### 11. 9로 나눈 나머지
```java
class Solution {
    public int solution(String number) {
        int answer = 0;
        
        for(String num : number.split("")) {
            answer +=Integer.parseInt(num);
        }
        answer %= 9;
        return answer;
    }
}
```

### 12. 덧셈식 출력하기
```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int a = sc.nextInt();
        int b = sc.nextInt();

        System.out.println(a + " + " + b + " = "+ (a+b));
    }
}
```

### 13. 배열의 원소 삭제하기
```java
import java.util.*;
class Solution {
    public ArrayList<Integer> solution(int[] arr, int[] delete_list) {
        ArrayList<Integer> result=new ArrayList<>();
        ArrayList<Integer> deleteList=new ArrayList<>();
        
        for(int d:delete_list){
            deleteList.add(d);
        }
        
        for(int a:arr){
            if(!deleteList.contains(a)){
                 result.add(a);
            }
        }
        return result;
    }
}
```

### 14. 공백으로 구분하기 1
```java
class Solution {
    public String[] solution(String my_string) {
        return my_string.split(" ");
    }
}
```

### 15. 부분 문자열
```java
class Solution {
    public int solution(String str1, String str2) {
        return str2.contains(str1) ? 1 : 0;
    }
}
```

### 16. 꼬리 문자열
```java
class Solution {
    public String solution(String[] str_list, String ex) {
        String answer = "";
        for(String str : str_list) {
            if(!str.contains(ex)) {
                answer += str;
            }
        }       
        return answer;
    }
}
```

### 17. x 사이의 개수
```java
import java.util.*;
class Solution {
    public ArrayList<Integer> solution(String myString) {
        ArrayList<Integer> answer =new ArrayList<>();
        String[] arr=myString.split("x");
        
        for(int i=0;i<arr.length;i++){    
            answer.add(arr[i].length());
        }
        
        if(myString.substring(myString.length()-1).equals("x")){
            answer.add(0);
        }
        return answer;
    }
}
```

### 18. 0 떼기
```java
class Solution {
    public String solution(String n_str) {
           return n_str.replaceFirst("^0+","");
    }
}
```

### 19. 부분 문자열인지 확인하기
```java
class Solution {
    public int solution(String my_string, String target) {
        return my_string.contains(target) ? 1 : 0;
    }
}
```

### 20. 특별한 이차원 배열 2
```java
class Solution {
    public int solution(int[][] arr) {
        int answer = 1;
        
        for(int i = 0 ; i < arr.length ; i++) {
            for(int j = 0 ; j < arr.length ; j++) {
                if(arr[i][j] != arr[j][i]) return 0;
            }
        }
        return answer;
    }
}
```

### 21. 정수 찾기
```java
class Solution {
    public int solution(int[] num_list, int n) {
        for(int a:num_list){
            if(a==n) return 1;
        }
        return 0;
    }
}
```

### 22. 주사위 게임 2
```java
class Solution {
    public int solution(int a, int b, int c) {
        if(a==b && b==c){
            return (a+b+c)*(a*a+b*b+c*c)*(a*a*a+b*b*b+c*c*c);
        }else if(a!=b && b!=c &&a!=c){
            return a+b+c;
        }else{
            return (a+b+c)*(a*a+b*b+c*c);
        }
    }
}
```

### 23. 뒤에서 5등 위로
```java
import java.util.*;

class Solution {
    public int[] solution(int[] num_list) {
        Arrays.sort(num_list);
        int[] answer = Arrays.copyOfRange(num_list, 5, num_list.length);
        
        return answer;
    }
}
```

### 24. 문자열 곱하기
```java
class Solution {
    public String solution(String my_string, int k) {
        String answer = my_string.repeat(k);
        return answer;
    }
}
```

### 25. 홀짝 구분하기
```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        
        if(n % 2 == 0) {
            System.out.println(n + " is even");
        } else {
            System.out.println(n + " is odd");
        }
    }
}
```

### 26. 이어 붙인 수
```java
class Solution {
    public int solution(int[] num_list) {
        String odd = "";
        String even = "";
        
        for(int num : num_list) {
            if(num % 2 == 1) {
                odd += num;
            } else {
                even += num;
            }
        }
        return Integer.parseInt(odd) + Integer.parseInt(even);
    }
}
```

### 27. 홀짝에 따라 다른 값 반환하기
```java
class Solution {
    public int solution(int n) {
        int answer = 0;
        
        if(n % 2 != 0) {
            for(int i = 1 ; i <= n ; i+=2) {
                answer += i;
            }
        } else {
            for(int i = 0 ; i <= n ; i+=2) {
                answer += i*i;
            }
        }
        return answer;
    }
}
```

### 28. 문자열 붙여서 출력하기
```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String a = sc.next();
        String b = sc.next();
        
        System.out.println(a+b);
    }
}
```

### 29. 더 크게 합치기
```java
class Solution {
    public int solution(int a, int b) {
        int ab = Integer.parseInt(a + "" + b);
        int ba = Integer.parseInt(b + "" + a);     
        if(ab > ba) {
            return ab;
        } else {
            return ba;
        }
    }
}
```

### 30. n의 배수
```java
class Solution {
    public int solution(int num, int n) {
        return num % n == 0 ? 1 : 0;
    }
}
```