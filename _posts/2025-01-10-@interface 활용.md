---
layout: post
---

@interface를 사용하여 사용자 정의 어노테이션을 생성할 수 있다

## 메타 어노테이션: 어노테이션을 위한 어노테이션

@Retention

```java
@Retention(SOURCE)    어노테이션이 소스 코드에만 이용 가능하며 컴파일 후에는 사라짐
@Retention(CLASS)     어노테이션이 .class 파일에 존재하지만 런타임 시에는 사라짐
@Retention(RUMTIME)   어노테이션이 컴파일러와 런타임에 사용 가능
```

@Target

```java
@Target(ElementType.TYPE)               클래스의 어떤 요소에나 적용 가능, 기본값
@Target(ElementType.FIELD)              클래스의 특정 필드
@Target(ElementType.METHOD)             클래스의 메서드
@Target(ElementType.PARAMETER)          메서드의 파라미터
@Target(ElementType.CONSTRUCTOR)        생성자
@Target(ElementType.LOCAL_VARIABLE)     로컬 변수
@Target(ElementType.ANNOTATION_TYPE)    어노테이션 타입
```

@Inherited<br>
어노테이션 정보가 서브 클래스에도 상속가능 여부


<br>
<br>


## 예시

@SpringBootApplication 어노테이션

```java
package com.ryan.spring_boot_rest_api;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class SpringBootRestApiApplication {
	public static void main(String[] args) {
		SpringApplication.run(SpringBootRestApiApplication.class, args);
	}
}
```

```java
@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
@Documented
@Inherited
@SpringBootConfiguration
@EnableAutoConfiguration
@ComponentScan(excludeFilters = { @Filter(type = FilterType.CUSTOM, classes = TypeExcludeFilter.class),
		@Filter(type = FilterType.CUSTOM, classes = AutoConfigurationExcludeFilter.class) })
public @interface SpringBootApplication {
...
}
```
