---
title: "JAVA 알고리즘 기초 40문제"
categories: [Ureca, Algorithm]
tags: [java, ArrayList]
image:
  path: /assets/post/2025/ureca/day14.png
  alt: java
published: true
---

팀별로 40문제 푸는게 오늘 팀 스터디였다. 솔직히 너무 많아서 힘들었다. ㅜㅜ  <br/>
하지만 헷갈리던 자바 문법이(특히 배열) 좀 익숙해진거같아 좋았다 !<br/>
근데.. !!  입문 20문제 푸는걸 과제로 받았다.............<br/>

하루에 알고리즘 60 문제 푸는 사람이 되었다 ! 

---

### 1 문자열을 정수로 변환하기
```java
class Solution {
    public int solution(String n_str) {
        return Integer.parseInt(n_str);
    }
}
```

### 2 문자열 정수의 합
```java
class Solution {
    public int solution(String num_str) {
        int answer = 0;
        
        for(int s : num_str.toCharArray()) {
            answer += s - '0';
        }
        
        return answer;
    }
}
```

### 3 정수 부분
```java
class Solution {
    public int solution(double flo) {
        return (int)flo;
    }
}
```

### 4 뒤에서 5등까지
```java
import java.util.Arrays;

class Solution {
    public int[] solution(int[] num_list) {
        Arrays.sort(num_list);

        return Arrays.copyOfRange(num_list, 0, 5);
    }
}
```

### 5 배열의 길이에 따라 다른 연산하기
```java
class Solution {
    public int[] solution(int[] arr, int n) {
        
        if(arr.length % 2 == 1) {
            for(int i = 0 ; i < arr.length ; i+=2) {
                arr[i] = arr[i] + n;
            }
        } else {
            for(int i = 1 ; i < arr.length ; i+=2) {
                arr[i] = arr[i] + n;
            }
        }
        return arr;
    }
}
```

### 6 배열 비교하기
```java
class Solution {
    public int solution(int[] arr1, int[] arr2) {
        int answer = 0;
        if(arr1.length > arr2.length) {
            return 1;
        } else if (arr1.length < arr2.length) {
            return -1;
        } 
        
        int sum1 = 0, sum2 = 0;
        for(int i = 0 ; i < arr1.length ; i++) {
            sum1 += arr1[i];
            sum2 += arr2[i];
        }
        
        if(sum1 > sum2) {
            return 1;
        } else if (sum1 < sum2) {
            return -1;
        } else {
            return 0;
        }       
    }
}
```

### 7 배월의 원소만큼 추가하기
```java
import java.util.ArrayList;

class Solution {
    public ArrayList<Integer> solution(int[] arr) {
        ArrayList<Integer> answer = new ArrayList<>();
        
        for(int i : arr) {
            for(int j = 0; j < i ; j++) {
                answer.add(i);
            }
        }
        
        return answer;
    }
}
```

### 8 rny_string
```java
class Solution {
    public String solution(String rny_string) {
        return rny_string.replace("m", "rn");
    }
}
```

### 9 문자열 바꿔서 찾기
```java
class Solution {
    public int solution(String myString, String pat) {
        String answer = "";
        myString = myString.replace("A", "a").replace("B", "A").replace("a", "B");
        return myString.contains(pat) ? 1 : 0;

    }
}
```

### 10 공백으로 구분하기2
```java
class Solution {
    public String[] solution(String my_string) {
        String[] strArr = my_string.trim().split("\\s+");
        return strArr;
    }
}
```

### 11 특정한 문자를 대문자로 바꾸기
```java
class Solution {
    public String solution(String my_string, String alp) {
        return my_string.replace(alp, alp.toUpperCase());
    }
}
```

### 12 A 강조하기
```java
class Solution {
    public String solution(String myString) {        
        return myString.toLowerCase().replace("a", "A");
    }
}
```

### 13 배열에서 문자열 대소문자 변환하기
```java
class Solution {
    public String[] solution(String[] strArr) {
        
        String[] answer = new String[strArr.length];
        
        for(int i = 0; i < strArr.length; i++) {
            if(i % 2 == 0) answer[i] = strArr[i].toLowerCase();
            else answer[i] = strArr[i].toUpperCase();
        }
        return answer;
    }
}
```

### 14 소문자로 바꾸기
```java
class Solution {
    public String solution(String myString) {
        return myString.toLowerCase();
    }
}
```

### 15 대문자로 바꾸기
```java
class Solution {
    public String solution(String myString) {
        return myString.toUpperCase();
    }
}
```

### 16 원하는 문자열 찾기
```java
class Solution {
    public int solution(String myString, String pat) {
        int answer = myString.toLowerCase().contains(pat.toLowerCase()) ? 1 : 0;
        return answer;
    }
}
```

### 17 길이에 따른 연산
```java
class Solution {
    public int solution(int[] num_list) {
        int answer = 0;
        
        if(num_list.length >= 11) {
            for(int num : num_list) {
                answer += num;
            }
        } else {
            answer = 1;
            for(int num : num_list) {
                answer *= num;
            }
        }
        
        return answer;
    }
}
```

### 18 조건에 맞게 수열 변환하기 1
```java
class Solution {
    public int[] solution(int[] arr) {
        int[] answer = new int[arr.length];
        answer = arr;
        for(int i = 0 ; i < arr.length ; i++) {
            if(arr[i] >= 50 && arr[i] % 2 == 0) {
                answer[i] = arr[i] / 2;
            } else if (arr[i] < 50 && arr[i] % 2 != 0) {
                answer[i] = arr[i] * 2;
            }
        }
        
        return answer;
    }
}
```

### 19 n보다 커질 때까지 더하기
```java
class Solution {
    public int solution(int[] numbers, int n) {
        int answer = 0;
        
        for(int num : numbers) {
            answer += num;
            if(answer > n) return answer;
        }
        
        return answer;
    }
}
```

### 20 할 일 목록
```java
import java.util.ArrayList;

class Solution {
    public ArrayList<String> solution(String[] todo_list, boolean[] finished) {
        ArrayList<String> answer = new ArrayList<>();
        for(int i = 0 ; i < todo_list.length ; i++) {
            if(!finished[i]) answer.add(todo_list[i]);
        }
        return answer;
    }
}
```

### 21 5명씩
```java
import java.util.ArrayList;

class Solution {
    public ArrayList<String> solution(String[] names) {
        ArrayList<String> answer = new ArrayList<>();
        
        for(int i = 0 ; i < names.length ; i+=5) {
            answer.add(names[i]);
        }
        
        return answer;
    }
}
```

### 22 홀수 vs 짝수
```java
class Solution {
    public int solution(int[] num_list) {
        int a = 0;  
        int b = 0; 
        
        for (int i = 0; i < num_list.length; i++) {
            if (i % 2 == 0) {  
                a += num_list[i];
            } else {  
                b += num_list[i];
            }
        }
        return a>b?a:b;
    }
}
```

### 23 n개 간격의 원소들
```java
import java.util.ArrayList;

class Solution {
    public ArrayList<Integer> solution(int[] num_list, int n) {
        ArrayList<Integer> answer = new ArrayList<>();
        
        for(int i = 0; i < num_list.length ; i+=n) {
            answer.add(num_list[i]);
        }
        return answer;
    }
}
```

### 24 n번째 원소까지
```java
import java.util.ArrayList;

class Solution {
    public ArrayList<Integer> solution(int[] num_list, int n) {
        ArrayList<Integer> answer = new ArrayList<>();
        
        for(int i = 0; i < n ; i++) {
            answer.add(num_list[i]);
        }
        
        return answer;
    }
}
```

### 25 순서 바꾸기
```java
class Solution {
    public int[] solution(int[] num_list, int n) {
        int[] answer = new int[num_list.length];
        
        for(int i = n, j = 0 ; i < num_list.length ; i++, j++) {
            answer[j] = num_list[i];
        }
        
        for(int i = 0, j = num_list.length - n ; j < num_list.length ; i++, j++) {
            answer[j] = num_list[i];
        }

        return answer;
    }
}
```

### 26 n번째 원소부터
```java
import java.util.ArrayList;

class Solution {
    public ArrayList<Integer> solution(int[] num_list, int n) {
        ArrayList<Integer> answer = new ArrayList<>();
        
        for(int i = 0; i < n ; i++) {
            answer.add(num_list[i]);
        }
        
        return answer;
    }
}
```

### 27 첫번째로 나오는 음수
```java
class Solution {
    public int solution(int[] num_list) {
        int answer = -1;
        
        for(int i = 0 ; i < num_list.length; i++) {
            if(num_list[i] < 0) {
                return i;
            }
        }
        return answer;
    }
}
```

### 28 가까운 1 찾기
```java
class Solution {
    public int solution(int[] arr, int idx) {
        int answer = -1;
        
        for(int i = idx ; i < arr.length ; i++) {
            if( arr[i] == 1) return i;    
        }
        
        return answer;
    }
}
```

### 29 카운트 다운
```java
class Solution {
    public int[] solution(int start_num, int end_num) {
        int[] answer = new int[start_num - end_num + 1];
        int j = 0;
        
        for(int i = start_num ; i > end_num - 1 ; i--) {
            answer[j++] = i;
        }
        return answer;
    }
}
```

### 30 배열 만들기 1
```java
class Solution {
    public int[] solution(int n, int k) {
        int[] answer = new int[n/k];
        int j = 0;
        
        for(int i = 1 ; i <= n ; i++) {
            if(i % k == 0) answer[j++] = i; 
        }
        return answer;
    }
}
```

### 31 접두사인지 확인하기
```java
class Solution {
    public int solution(String my_string, String is_prefix) {
        int answer = 0;
        
        if(my_string.length() < is_prefix.length()) return 0;
        if(is_prefix.equals(my_string.substring(0, is_prefix.length()))) return 1;
        
        return answer;
    }
}
```

### 32 문자열의 앞의 n글자
```java
class Solution {
    public String solution(String my_string, int n) {
        return my_string.substring(0, n);
    }
}
```

### 33 접미사인지 확인하기
```java
class Solution {
    public int solution(String my_string, String is_suffix) {
        int answer = 0;
        
        if(my_string.length() < is_suffix.length()) return 0;
        if(is_suffix.equals(my_string.substring(my_string.length() - is_suffix.length()))) return 1;
        
        return answer;

    }
}
```

### 34 접미사 배열
```java
import java.util.Arrays;

class Solution {
    public String[] solution(String my_string) {
        String[] answer = new String[my_string.length()];
        int j = 0;
        for(int i = 1 ; i <= my_string.length() ; i++) {
            answer[j++] = my_string.substring(my_string.length()-i,my_string.length());
        }
        
        Arrays.sort(answer);
        return answer;
    }
}
```

### 35 문자열의 뒤의 n글자
```java
class Solution {
    public String solution(String my_string, int n) {

        return my_string.substring(my_string.length() - n);
    }
}
```

### 36 부분 문자열 이어 붙여 문자열 만들기
```java
class Solution {
    public String solution(String[] my_strings, int[][] parts) {
        String answer = "";
        
        for(int i = 0 ; i < my_strings.length ; i++) {
            int s = parts[i][0];
            int e = parts[i][1];
            
            answer += my_strings[i].substring(s,e+1);
        }
        
        return answer;
    }
}
```

### 37 글자 이어 붙여 문자열 만들기
```java
class Solution {
    public String solution(String my_string, int[] index_list) {
        String answer = "";
        
        for(int idx : index_list) {
            answer += my_string.split("")[idx];
        }
        return answer;
    }
}
```

### 38 콜라츠 수열 만들기
```java
import java.util.ArrayList;

class Solution {
    public ArrayList<Integer> solution(int n) {
        ArrayList<Integer> answer = new ArrayList<>();
        
        answer.add(n);
        while(n != 1) {
            if(n % 2 == 0) {
                n /= 2;
            } else {
               n = 3*n+1;
            }
            answer.add(n);
        }
        
        return answer;
    }
}
```

### 39 카운트 업
```java
class Solution {
    public int[] solution(int start_num, int end_num) {
        int[] answer = new int[end_num - start_num +1];
        int j = 0;
        
        for(int i = start_num ; i < end_num + 1 ; i++) {
            answer[j++] = i;
        }
        
        return answer;
    }
}
```

### 40 수 조작하기
```java
class Solution {
    public String solution(int[] numLog) {
        String answer = "";
        
        for(int i = 0 ; i < numLog.length - 1 ; i++) {
            int num = numLog[i+1] - numLog[i];
            
            switch(num) {
                case 1:
                    answer += "w";
                    break;
                case -1:
                    answer += "s";
                    break;
                case 10:
                    answer += "d";
                    break;
                case -10:
                    answer += "a";
                    break;
                default:
                    break;
            }
        }
        return answer;
    }
}
```
