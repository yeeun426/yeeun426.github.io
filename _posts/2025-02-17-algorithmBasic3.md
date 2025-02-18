---
title: "JAVA 알고리즘 기초 30문제"
categories: [Ureca, Algorithm]
tags: [java, ArrayList]
image:
  path: /assets/post/2025/ureca/day16.png
  alt: java
published: true
---

## 1. 두수의 연산값 비교하기
```java
class Solution {
    public int solution(int a, int b) {
        int answer = 0;
        
        String str = a + "" + b;
        int sum = 2 * a * b;
        
        return Math.max(Integer.parseInt(str), sum);
    }
}
```

## 2. 문자열로 변환
```java
class Solution {
    public String solution(int n) {
        String answer = "";
        return answer + n;
    }
}
```

## 3. flag에 따라 다른 값 반환하기
```java
class Solution {
    public int solution(int a, int b, boolean flag) {
        return flag ? a + b : a - b;
    }
}
```

## 4. 공배수
```java
class Solution {
    public int solution(int number, int n, int m) {
        return number % n == 0 && number % m == 0 ? 1: 0;
    }
}
```

## 5. 배열 만들기 3
```java
import java.util.Arrays;

class Solution {
    public int[] solution(int[] arr, int[][] intervals) {
        
        int[] arr1 = Arrays.copyOfRange(arr, intervals[0][0], intervals[0][1] + 1);
        int[] arr2 = Arrays.copyOfRange(arr, intervals[1][0], intervals[1][1] + 1);
        
        int[] answer = new int[arr1.length + arr2.length];
        
        for(int i = 0; i < arr1.length; i++) answer[i] = arr1[i];
        int j = 0;
        for(int i = arr1.length; i < answer.length; i++) answer[i] = arr2[j++];
        
        return answer;
    }
}
```

## 6. 문자열 잘라서 졍렬하기
```java
import java.util.*;

class Solution {
    public ArrayList<String> solution(String myString) {
        
        ArrayList<String> answer = new ArrayList<>();
        String[] str = myString.split("x");
        
        for(String s:str) 
            if(!s.isEmpty()) answer.add(s);
        
        Collections.sort(answer);
        return answer;
    }
}
```

## 7. 배열의 길이를 2의 거듭제곱으로 만들기
```java
class Solution {
    public int[] solution(int[] arr) {
        int length = 1;        
        while(length < arr.length) length *= 2;

        int[] answer = new int[length];

        for(int i = 0 ; i < arr.length ; i++) {
            answer[i] = arr[i];
        }
        return answer;
    }
}
```

## 8. 문자열이 몇 번 등장하는지 세기
```java
class Solution {
    public int solution(String myString, String pat) {
        int answer = 0;
        int strLength = myString.split("").length;
        int patLength = pat.split("").length;
        
        for(int i = 0 ; i < strLength - patLength + 1 ; i++) {
            if(myString.substring(i, i + patLength).equals(pat))  {
                answer++;
            }
        }
        return answer;
    }
}
```

## 9. 특정 문자열로 끝나는 가장 긴 부분 문자열 찾기
```java
class Solution {
    public String solution(String myString, String pat) {
        String answer = "0";
        int strLength = myString.split("").length; 
        int patLength = pat.split("").length;
        
        for(int i = strLength; i >= patLength ; i--) {
            if(myString.substring(i - patLength, i ).equals(pat))  {
                answer = myString.substring(0, i);
                break;
            }
        }
        // 다른 사람 풀이
        // String answer = "";
        // int idx = myString.lastIndexOf(pat);
        // answer = myString.substring(0, idx) + pat;
        // return answer;

        return answer;
    }
}

```

## 10. 1로 만들기
```java
class Solution {
    public int solution(int[] num_list) {
        int answer = 0;
            
        for(int num : num_list) {
            int cnt = 0;
            while(num > 1) {
                cnt++;
                num /= 2;
            }
            answer += cnt;
        }
        return answer;
    }
}
```

## 11. 문자열 뒤집기
```java
class Solution {
    public String solution(String my_string, int s, int e) {
        StringBuffer str = new StringBuffer(my_string.substring(s,e+1));
        return my_string.substring(0,s) + str.reverse().toString() + my_string.substring(e+1);
    }
}
```

## 12. 배열 만들기 5
```java
import java.util.ArrayList;

class Solution {
    public ArrayList<Integer> solution(String[] intStrs, int k, int s, int l) {
        ArrayList<Integer> answer = new ArrayList<>();
        for(String str : intStrs) {
            int num = Integer.parseInt(str.substring(s, s+l));
            if(num > k) answer.add(num);
        }
        return answer;
    }
}
```

## 13. 수열과 구간 쿼리 3
```java
class Solution {
    public int[] solution(int[] arr, int[][] queries) {        
        for (int[] query : queries) {
            int i = query[0], j = query[1];
            int temp = arr[i]; 
            arr[i] = arr[j];
            arr[j] = temp;
        }
        return arr;
    }
}
```

## 14. 빈 배열에 추가, 삭제하기
```java
import java.util.ArrayList;

class Solution {
    public int[] solution(int[] arr, boolean[] flag) {
        String str = "";
        
        for(int i = 0 ; i < flag.length ; i++) {
            if(flag[i]) {
                str += (arr[i] + "").repeat(arr[i] * 2);
            } else {
                str = str.substring(0, str.length() - arr[i]);
            }
        }   
        
        int[] answer = new int[str.length()];
        
        for(int i = 0 ; i < answer.length ; i++) {
            answer[i] = Integer.parseInt(str.split("")[i]);
        }
        
        return answer;
    }
}
```

## 15. ad 제거하기
```java
import java.util.*;

public class Solution {
    public String[] solution(String[] strArr) {
        ArrayList<String> str = new ArrayList<>();  
        for (String s : strArr) {
            if (!s.contains("ad")) {  
                str.add(s);
            }
        }
        String[] answer=str.toArray(new String[str.size()]);
        return answer;

    }
}
```

## 16. 날짜 비교하기
```java
public class Solution {
    public int solution(int[] date1, int[] date2) {
        
        if (date1[0] < date2[0]) {
            return 1;  
        } else if (date1[0] > date2[0]) {
            return 0;  
        } else {
            if (date1[1] < date2[1]) {
                return 1; 
            } else if (date1[1] > date2[1]) {
                return 0; 
            } else {
                if (date1[2] < date2[2]) {
                    return 1;  
                } else {
                    return 0; 
                }
            }
        }
    }
}
```

## 17. 수열과 구간 쿼리 1
```java
public class Solution {
    public int[] solution(int[] arr, int[][] queries) {
        for (int[] q : queries) {
            int s = q[0];  
            int e = q[1];  
           
            for (int i = s; i <= e; i++) {
                arr[i] += 1;
            }
        }
        return arr;  
    }
}
```

## 18. 글자 지우기
```java
public class Solution {
    public String solution(String my_string, int[] indices) {
        String answer = "";
        for (int i = 0; i < my_string.length(); i++) {   
            int a = 0;
            for (int x : indices) {
                if (x == i) {
                    a=1;
                    break;
                }
            }
            if (a==0) {
                answer += my_string.charAt(i);
            }
        }
        return answer;
    }
}
```

## 19. 등차수열의 특정한 항만 더하기
```java
class Solution {
    public int solution(int a, int d, boolean[] included) {
        int answer = 0;
        for(int i=0;i<included.length;i++){
            int x=a+i*d;   
            if(included[i]==true){
                answer+=x;
            }
        }
        return answer;
    }
}
```

## 20. 문자열 섞기
```java
class Solution {
    public String solution(String str1, String str2) {
        String answer = "";
        for(int i=0;i<str1.length();i++){
            answer+=str1.charAt(i);
            answer+=str2.charAt(i);
        }
        return answer;
    }
}
```

## 21. 이차원 배열 대각선 순회하기
```java
class Solution {
    public int solution(int[][] board, int k) {
        int answer = 0;
        for(int i=0;i<board.length;i++){
            for(int j=0;j<board[i].length;j++){
                if(i+j<=k){
                    answer+=board[i][j];
                }
            }
        }
        return answer;
    }
}
```

## 22. 세로읽기
```java
class Solution {
    public String solution(String my_string, int m, int c) {
        String answer = "";       
        for(int i = c - 1; i < my_string.length(); i += m){
            answer+=my_string.charAt(i);
        }     
        return answer;
    }
}
```

## 23. 문자열 묶기
```java
import java.util.Arrays;

class Solution {
    public int solution(String[] strArr) {
        int[] answer = new int[strArr.length];
      
        for(String s : strArr) {
            answer[s.length() -1]++;
        }
        return Arrays.stream(answer).max().getAsInt();
    }
}
```

## 24. 세 개의 구분자
```java
import java.util.Arrays;

class Solution {
    public String[] solution(String myStr) {
        String[] result = Arrays.stream(myStr.split("[abc]"))
            .filter(s -> !s.isEmpty())
            .toArray(String[]::new);
        
        return result.length != 0 ? result : new String[]{"EMPTY"};
    }
}
```

## 25. 2의 영역
```java
import java.util.Arrays;
import java.util.stream.IntStream;

class Solution {
    public int[] solution(int[] arr) {
        int[] indexes = IntStream.range(0, arr.length) // Python의 range와 비슷한 역할
           .filter(i -> arr[i] == 2) // 인덱스 뽑기
           .toArray();
        
        return indexes.length != 0 ? Arrays.copyOfRange(arr, indexes[0], indexes[indexes.length - 1] + 1): new int[]{-1};
    }
}
```

## 26. 리스트 자르기 
```java
import java.util.stream.IntStream;
import java.util.Arrays;

class Solution {
    public int[] solution(int n, int[] slicer, int[] num_list) {
        int a = slicer[0], b = slicer[1], c = slicer[2];
        int[] answer = {};

        if (n == 1) {
            answer = Arrays.copyOfRange(num_list, 0, b + 1);
        } else if (n == 2) {
            answer = Arrays.copyOfRange(num_list, a, num_list.length);
        } else if (n == 3) {
            answer = Arrays.copyOfRange(num_list, a, b + 1);
        } else if (n == 4) {
            answer = IntStream.range(a, b + 1)
                    .filter(i -> (i - a) % c == 0) // 간격에 해당하는 인덱스 뽑기
                    .map(i -> num_list[i])
                    .toArray();
        }
        return answer;
    }
}
```

## 27. 간단한 논리 연산
```java
class Solution {
    public boolean solution(boolean x1, boolean x2, boolean x3, boolean x4) {
        return (x1 || x2) && (x3 || x4);
    }
}
```

## 28. 문자열 반복해서 출력하기
```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String str = sc.next();
        int n = sc.nextInt();
      
        System.out.println(str.repeat(n));
    }
}
```

## 29. 커피 심부름
```java
class Solution {
    public int solution(String[] order) {
        int answer = 0;    
        for(String o : order) {
            if(o.contains("americano")) answer += 4500;
            else if(o.contains("latte")) answer += 5000;
            else answer += 4500;
        }
        return answer;
    }
}
```

## 30. 조건에 맞게 수열 변환하기 2
```java
import java.util.Arrays;

public class Solution {
    public int solution(int[] arr) {
        int[] previousArr;
        int x = 0;
        
        while (true) {
             previousArr = Arrays.copyOf(arr, arr.length);

            for (int i = 0; i < arr.length; i++) {
                if (arr[i] >= 50 && arr[i] % 2 == 0) {
                    arr[i] /= 2; 
                } else if (arr[i] < 50 && arr[i] % 2 != 0) {
                    arr[i] = arr[i] * 2 + 1;
                }
            }

            if (Arrays.equals(previousArr, arr)) {
                break;
            }
            x++;
        }
        return x;
    }
}
```

---

## END