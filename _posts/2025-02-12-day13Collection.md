---
title: "[Day13] Collections"
categories: [Ureca, Algorithm]
tags: [java, HashSet, List, ListLinked]
image:
  path: /assets/post/2025/ureca/collection.png
  alt: java
published: true
---

html과 spring을 어떻게 연결하는 과제인지 잘 이해가 안가서 일단 부족한 부분을 수정했다.
로그인, 회원가입 모달창을 넣었고, 반응형으로 수정했다.

<a src="https://raccoon-shop.netlify.app/"> https://raccoon-shop.netlify.app/</a>

---

# Collections

예시를 먼저 보고 정리를 해보려 한다.

## ArrayList & HashSet
```java
public class Test {
    public static void main(String[] args) {
        // ArrayList 예시
        ArrayList<String> list = new ArrayList<>();
        list.add("Apple");
        list.add("Banana");
        list.add("Orange");
        list.add("Apple"); // ❗️ 중복 허용
        System.out.println(list.size());  // 4
        System.out.println(list);         // [Apple, Banana, Orange, Apple]

        // HashSet 예시 (중복 제거)
        HashSet<Object> set = new HashSet<>();
        String s1 = new String("Apple");
        set.add(s1);
        set.add("Banana");
        set.add("Orange");
        String s2 = new String("Apple");
        set.add(s2); // ❗️ "Apple"은 중복이라 추가되지 않음
        set.add(new Object());
        set.add(new Object()); // ⭐️ Object는 항상 새로운 주소값을 가지므로 중복 X

        // 사용자 정의 객체 `Member`
        Member m1 = new Member("이예은", 26);
        Member m2 = new Member("이예은", 26); // member에서 재정의 해둠

        set.add(m1);
        set.add(m2); // ❗️ 중복으로 추가되지 않음.

        System.out.println(set.size()); //  6 (중복된 "Apple" 제거, Object 2개, Member 1개)
        System.out.println(set);

        System.out.println(m1.hashCode());
        System.out.println(m2.hashCode()); // 같은 값
    }
}
```

> ❓❓ 사용자 객체랑 new Object는 중복이 추가 되고, new string은 안되는 이유 <br/>
> new Object()는 중복 추가 가능 -> Object는 기본적으로 hashCode()가 다름<br/>
> new String("Apple")은 중복 추가 안됨 -> String의 equals()와 hashCode()가 문자열 값으로 비교되기 때문

### POINT
- ArrayList는 순서를 유지하며 중복을 허용한다.
- HashSet은 중복을 허용하지 않고, 순서를 보장하지 않음.
- new Object()는 항상 새로운 주소값을 가지므로 중복 제거되지 않음.
- Member 객체가 중복으로 인식되지 않으려면 hashCode()와 equals()를 재정의해야 함.

## Member 클래스 (Comparable 구현 & hashCode(), equals() 재정의)
```java
public class Member implements Comparable<Member> {
    private String name;
    private int age;    

    public Member(String name, int age) {
        setName(name);
        setAge(age);
    }

    public String getName() { return name; }
    public void setName(String name) {
        if (name != null) {
            this.name = name;
        } else {
            System.out.println("null은 불가");
        }
    }

    public int getAge() { return age; }
    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "Member [name=" + name + ", age=" + age + "]";
    }

    // ✅ 정렬 기준 정의 (나이 오름차순 → 이름 오름차순)
    @Override
    public int compareTo(Member o) {
        if (this.age != o.getAge()) {
            return this.age - o.getAge(); 
        }
        return this.name.compareTo(o.getName());
    }

    // ✅ HashSet에서 중복 제거를 위해 `hashCode()`와 `equals()` 재정의
    @Override
    public int hashCode() {
        return name.hashCode() + age;
    }

    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (!(obj instanceof Member)) return false;
        Member other = (Member) obj;
        return this.name.equals(other.name) && this.age == other.age;
    }
}
```

### POINT
- compareTo()를 구현하여 나이 오름차순 → 이름 오름차순으로 정렬.
- hashCode()와 equals()를 재정의하여 중복 제거 가능하게 함.

### compareTo() 메서드란?
compareTo()는 두 객체를 비교하는 메서드로, 비교 결과에 따라 다음 값을 반환
- 0: 두 객체가 같다고 판단.
- 양수: 현재 객체가 o 객체보다 크다고 판단.
- 음수: 현재 객체가 o 객체보다 작다고 판단.

```java
// compareTo() 메서드 정의
@Override
public int compareTo(Member o) {
    // 나이가 적은 사람을 먼저 오게 정렬
    return Integer.compare(this.age, o.age);
}
```

## ArrayList

```java
public class ArrayListTest {
    public static void main(String[] args) {
        ArrayList<Member> list = new ArrayList<>();

        Member m1 = new Member("이예은", 26);
        Member m2 = new Member("홍길동", 20);
        Member m3 = new Member("이영애", 45);

        list.add(m1);
        list.add(m2);
        list.add(m3);

        System.out.println(list.size()); // 3
        System.out.println(list);        
// [Member [name=이예은, age=26], Member [name=홍길동, age=20], Member [name=이영애, age=45]]
        Collections.sort(list); // 정렬 (compareTo() 기준)
        System.out.println(list);        
// [Member [name=홍길동, age=20], Member [name=이예은, age=26], Member [name=이영애, age=45]]
    }
}
```

### POINT
- Collections.sort(list);를 사용하여 compareTo() 기준으로 정렬 가능.

## LinkedList

```java
public class LinkedListTest {
    public static void main(String[] args) {
        LinkedList<Member> list = new LinkedList<>();

        list.add(new Member("이예은", 26));
        list.add(new Member("홍길동", 20));
        list.add(new Member("이영애", 45));

        System.out.println(list.size()); // 3
        System.out.println(list);
// [Member [name=이예은, age=26], Member [name=홍길동, age=20], Member [name=이영애, age=45]]

        Collections.sort(list); 
        System.out.println(list);
// [Member [name=홍길동, age=20], Member [name=이예은, age=26], Member [name=이영애, age=45]]
    }
}
```

### POINT
- LinkedList도 ArrayList와 동일하게 정렬

## HashSet
```java
package collections;
import java.util.*;

public class HashSetTest {
    public static void main(String[] args) {
        HashSet<Member> set = new HashSet<>();

        set.add(new Member("전은수", 38));
        set.add(new Member("이예은", 26));
        set.add(new Member("홍길동", 30));
        set.add(new Member("이예은", 26)); // ❌ 중복 제거됨

        System.out.println(set.size());
        System.out.println(set); 
// [Member [name=이예은, age=26], Member [name=전은수, age=38], Member [name=홍길동, age=30]]

        // `HashSet`을 정렬하려면 `ArrayList`로 변환 후 정렬
        List<Member> list = new ArrayList<>(set);
        Collections.sort(list);
        System.out.println(list);
// [Member [name=이예은, age=26], Member [name=홍길동, age=30], Member [name=전은수, age=38]]
    }
}
```
### POINT
- HashSet은 정렬되지 않음 → ArrayList로 변환 후 정렬해야 함.

## TreeSet (자동 정렬)
```java
public class TreeSetTest {
    public static void main(String[] args) {
        TreeSet<Member> set = new TreeSet<>();

        set.add(new Member("이예은", 26));
        set.add(new Member("홍길동", 20));
        set.add(new Member("이영애", 45));
        set.add(new Member("이예은", 26)); // ❌ 중복 제거됨

        System.out.println(set.size());
        System.out.println(set); // 자동 정렬됨
    }
}
```
### POINT
- TreeSet은 추가될 때 자동 정렬됨 (compareTo() 기준).

## HashMap (Key-Value 저장)
```java
public class HashMapTest {
    public static void main(String[] args) {
        Map<String, Member> map = new HashMap<>();

        map.put("이예은", new Member("이예은", 38));
        map.put("홍길동", new Member("홍길동", 20));
        map.put("이영애", new Member("이영애", 45));
        map.put("이예은", new Member("이예은", 28)); // 기존 값 덮어쓰기

        System.out.println(map.size()); // 3
        System.out.println(map);
    }
}
```
### point
- HashMap은 Key 중복 불가 → 기존 값 덮어쓰기.

✅ 실무에서는 set보단 list를 많이씀 -> 정렬도 되기 때문

## SUMMARY

| collection  | 특징                 | 중복 허용 | 정렬 지원             |
|-------------|----------------------|-----------|-----------------------|
| ArrayList   | 순서 유지, 빠른 조회  | ✅ O      | ❌ (정렬 필요)         |
| LinkedList  | 빠른 삽입/삭제        | ✅ O      | ❌ (정렬 필요)         |
| HashSet     | 중복 제거, 빠른 검색  | ❌ X      | ❌                    |
| TreeSet     | 중복 제거, 자동 정렬  | ❌ X      | ✅ (자동 정렬)         |
| HashMap     | Key-Value 저장, 빠른 검색 | Key ❌, Value ✅ | ❌                    |
| TreeMap     | Key-Value 저장, 자동 정렬 | Key ❌, Value ✅ | ✅ (Key 기준 자동 정렬) |


- List는 순서가 있고 중복을 허용하지만, Set은 중복을 허용하지 않음.
- HashSet은 중복 제거, TreeSet은 자동 정렬.
- HashMap은 Key-Value 저장, TreeMap은 Key 기준 자동 정렬.
- Comparable<T>을 구현하면 정렬 가능, hashCode()와 equals()를 올바르게 구현하면 HashSet에서 중복 제거 가능.

---

## Study
💡 회원가입 클릭 시, 배열에 모든 고객정보 확인가능하게 하기
### payload에 찍힌 id, pw 값 (제대로 서버와 통신한 것)
<img src="/assets/post/2025/ureca/day12.png" alt='' width=1300px>

### 아이디값 중복 허용하지 않는 배열로 찍힌다. -> HashMap 사용
<img src="/assets/post/2025/ureca/collections2.png" alt='' width=1300px>

```java
package come.lye.shop.controller;

import org.springframework.web.bind.annotation.RestController;

import java.util.ArrayList;
import java.util.HashMap;

import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;

import come.lye.shop.dto.Member;

@RestController
public class MemberController {
	// ArrayList<Member> list = new ArrayList<>();
	HashMap<String, Member> map = new HashMap<>(); // email 중복 안됨
	
	@PostMapping("insertMember")
	public void insertMember(@RequestBody Member member) {
		System.out.println(member);
		// list.add(member);
		map.put(member.getEmail(),member);
		System.out.println(map);
	}
}
```

---

## END