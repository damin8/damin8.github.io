---
layout:     post
title:      "Association"
subtitle:   "연관 관계란? 및 코드"
date:       2019-09-03 21:43:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: Software_Engineering
tags:
  - Software_Engineering
---

## 연관 관계

- 연관된 클래스 상에 **실선**을 그어 표시
- 두 클래스 사이의 관계가 명확한 경우에 이름을 사용안해도 됨
- 각 클래스 객체의 역할은 클래스 바로 옆 선 가까이 기술
- 역할 이름은 연관된 클래스의 객체들이 서로 참조할 수 있는 속성의 이름으로 활용

![그림1-9](/img/in-post/Software/그림1-9.PNG)</br>

#### 체크 포인트

![26쪽CP](/img/in-post/Software/26쪽CP.PNG)</br>

~~~
public class Person
    {
        private Phone[] phones;
        
        public Person()
        {
            phones = new Phone[2];
        }
        public Phone[] getPhone()
        {
            return phones;
        }
    }
    
public class Phone
    {

    }
~~~

![27쪽CP](/img/in-post/Software/27쪽CP.PNG)</br>

~~~
   public class Person
    {
        private Phone HomePhones;
        private Phone OfficePhones;
        public Phone homePhone
        {
            get => HomePhones;
            set => HomePhones = value;
        }
        public Phone officePhones
        {
            get => OfficePhones;
            set => OfficePhones = value;
        }
    }
  public class Phone
    {

    }
~~~

## 다중성

![다중성](/img/in-post/Software/다중성.PNG)</br>

- 1명의 교수, 1명 이상의 학생.
- 1명의 학생이 2명 이상의 교수한테 상담 못받음.

### 양방향 연관 관계

- 두 클래스를 연결한 선에 화살표 x
- 서로의 존재를 인지

### 단방향 연관 관계

- 한쪽으로만 방향성이 있는 관계
- 한 쪽은 알지만 다른 쪽은 상대방의 존재를 모른다는 의미

#### 체크 포인트

![28쪽CP](/img/in-post/Software/28쪽CP.PNG)</br>

~~~
    public class Student
    {
        private List<Course> courses;
        public Student()
        {
            courses = null;
        }
        public void registerCourse(Course course)
        {
            courses.Add(course);
        }
        public void dropCourse(Course course)
        {
            courses.Remove(course);
        }
    }
    public class Course
    {
        
    }
~~~

![28쪽CP](/img/in-post/Software/28쪽CP.PNG)</br>

![29쪽답](/img/in-post/Software/29쪽답.PNG)</br>

### 연관 클래스

- 연관 관계에 추가할 속성이나 행위가 있을 때 사용

![그림1-13](/img/in-post/Software/그림1-13.PNG)</br>

Student에 저장

-> 홍길동, 신다민, etc..

Course에 저장

-> 영어, 수학, etc..

그럼 각 인원이 듣는 수업은? 홍길동에 대한 영어 성적은?

> 이래서 연관 클래스가 필요하다.

Transcript 객체는 Student 객체와 Course 객체를 연관시키는 객체

따라서 Student,Course 객체를 참조할 수 있는 속성을 포함해야 한다.

> ex) 홍길동이 수학에서 A+을 받았다.

연관 클래스를 일반 클래스로 변환하면?

> Student ㅡ Transcript ㅡ Course

- 사건 이력 표현

![그림1-15](/img/in-post/Software/그림1-15.PNG)</br>

Student가 오늘도 빌렸고, 1년전에도 빌렸어도 표현이 가능하다.

Borrowing 객체가 2개가 된다.

### 재귀적 연관 관계

- 재귀적 연간 관계란?

> 동일한 클래스에 속한 객체들의 관계

- 역할을 클래스로 할 때 문제가 생긴다.

만약 A가 B를 관리한다고 하자.

B가 C를 관리하면, B는 사원이면서 관리자이다.

이럴때 문제가 생겨서 생겨넌 것이 재귀적 연관 관계다.

문제의 원인 : 역할로 클래스를 나눴기 때문에

해결 : 역할로 연관 관계를 보자

![그림1-16](/img/in-post/Software/그림1-16.PNG)</br>

여기서도 문제점 !

재귀적으로 가다보면 루프가 생길 수 있다. (제약이 없기 때문에)

> ex) a -> b -> c -> a

![그림1-18](/img/in-post/Software/그림1-18.PNG)</br>

따라서 이렇게 제약을 설정해줘야 한다.

{} -> 제약 설정할 때 자연어로 수식을 달면 된다.





