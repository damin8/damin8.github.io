---
layout:     post
title:      "Spring Boot + MariaDB + MyBatis (2)"
subtitle:   "Spring Boot, MariaDB, MyBatis 연동하기"
date:       2020-07-22 10:03:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: Spring
tags:
  - Spring
  - MariaDB
  - MyBatis
---

## 환경

- Spring Boot 2.2.5
- Ubuntu 18.04
- MariaDB
- IntelliJ

### Gradle

```
implementation 'org.mybatis.spring.boot:mybatis-spring-boot-starter:2.1.3'
implementation 'org.mariadb.jdbc:mariadb-java-client:2.6.1'
```

각 버전은 원하는 버전을 입력하면 된다.

> 소소한 팁 : ctrl + shift 를 누르면 최신순으로 버전이 뜬다🤞

### Application Properties

```
# Data Model의 package 경로
mybatis.type-aliases-package = com.hours22.devstudent.Entity

# .xml Mapper의 경로
mybatis.mapper-locations = mapper/*.xml

# MariaDB Driver
spring.datasource.driver-class-name=org.mariadb.jdbc.Driver

# MariaDB URL
# ex) mariadb://localhost:3306/test?characterEncoding=UTF-8&serverTimezone=UTC
spring.datasource.url=jdbc:mariadb://{ip}:{port}/{DB}?characterEncoding=UTF-8&serverTimezone=UTC

spring.datasource.username=22hours
spring.datasource.password=22hours
```

### Mapper Interface

```
@Repository
@Mapper
public interface CarMapper {

    void createTable();

    List<Car> findList();

    void saveCar(Car car);
}
```

- **@Repository** 를 붙이지 않으면 나중에 **@Autowired** 를 쓸때 빨간줄이 뜬다.

> 에러는 아니다. 실행해보면 정상 실행이 된다

- createTable() = Table 을 생성할 메서드

- findList() = Car List 출력

- saveCar(Car car) = Car 객체 저장

### Entity

```
@Getter
@Setter
@ToString
@AllArgsConstructor
public class Car {

    private String name;
    private String color;

}
```

### Mapper Service

```
@Service
public class MapperService {

    @Autowired
    public CarMapper mapper;

    public void saveCar(String name, String color) {
        Car car = new Car(name, color);

        mapper.save(Car);
    }

    public void createTable(){
        mapper.createTable();
    }

    public void findList() {
        mapper.findList().forEach(data -> System.out.println(data));
    }
}
```

### car-mapper.xml

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.hours22.devstudent.Repository.CarMapper">
    <select id="findList" resultType="car">
        SELECT name,
               color
        FROM car
    </select>

    <insert id="saveCar" parameterType="car">
        INSERT INTO car (name,
                         color)
        VALUES (#{name},
                #{color})
    </insert>
    <insert id="createTable">
        CREATE TABLE `car`
        (
            `name`  VARCHAR(20) NOT NULL,
            `color` VARCHAR(30) NOT NULL,
            PRIMARY KEY (`name`)
        )
    </insert>
</mapper>


```

- 주의 사항

1. CarMapper의 Method와 .xml의 id 는 같아야 한다.
1. application.properties 에 설정한 경로와 xml의 경로가 같아야 한다.
1. mapper namespace 경로 확인.

### Controller

```
@@RestController
@RequestMapping("/mapper/*")
public class CarContoller {
    @Autowired
    private MapperService mapperService;

    @RequestMapping(value = "/create/table",method = RequestMethod.GET)
    public void createTable(){
        alarmService.createTable();
    }

    @RequestMapping(value = "/create/car",method = RequestMethod.GET)
    public void createCar(){
        alarmService.saveCar("Audi","RED");
    }

    @RequestMapping(value = "/find/list",method = RequestMethod.GET)
    public void findList(){
        alarmService.findList();
    }
}
```

### 실행 & 결과

1. **http://localhost:8080(서버 포트)/mapper/create/table** 에 접속해서 table 생성
1. **http://localhost:8080(서버 포트)/mapper/create/car** 에 접속해서 car 생성
1. **http://localhost:8080(서버 포트)/mapper/find/list** 에 접속해서 car 출력

![1](/img/in-post/Spring/car.PNG)

![1](/img/in-post/Spring/car2.PNG)

- 정상적으로 작동 된다😁


<script src="https://utteranc.es/client.js" repo="damin8/blog-comment" issue-term="title" label="Comment" theme="github-light" crossorigin="anonymous" async>
</script>


