---
layout: post
title:  "[코틀린 기초] 1.함수 및 변수 선언"
date:   2015-04-18 08:43:59
author: Ben Centra
categories: Kotlin
cover:  "/assets/instacode.png"
---

# [코틀린 기초] 1. 함수 및 변수 선언
<br>
##### 본 포스트는 프로그래밍 언어에 대한 기본적인 이해가 있으신 분들을 대상으로 작성하였습니다.
<br>
이번에는 코틀린의 함수와 변수의 선언 방법과 사용 예제를 살펴보겠습니다.
<br>
<br>
## 1. 변수 선언



코틀린의 변수는 Assign-once variable과 Mutable variable로 구분하여 선언할 수 있습니다.

Assign-once variable은 말그대로 한번 값을 초기화하면 이후에 변경이 불가능한 변수입니다.

`val` 예약어를 사용해서 아래와 같은 형태로  Assign-once variable를 선언할 수 있습니다.

```kotlin
val seven: Int = 7
seven = 4   // 에러 발생 - 변경이 불가능하다.
```



Mutable variable은 값을 계속해서 변경 할 수 있는 변수로 `var` 예약어를 사용해서 선언할 수 있습니다.

```kotlin
var name: String = "양배추"
name = "조세호"

var age = 30 // 타입 추론
age += 1 // 더하기 대입연산자 사용가능
```

위 코드에서 특이한 부분이 하나 있는데 `age` 변수를 선언할 때 타입을 안써줬습니다.  코틀린에서는 대입되는 값으로 타입을 유추할 수 있는 경우 자동으로 알아서 타입을 지정하여 줍니다.

<br>

## 2.함수 선언



기본적인 함수는 아래와 같이 `fun` 예약어를 사용하여 선언할 수 있습니다.

``` kotlin
fun myFunction(a: Int, b: Int ): String {
	return (a * b).toString() //리턴 값을 String타입으로 변환
}
```

위의 함수는 `Int` 타입 인자 2개를 곱한 값을 `String` 타입으로 리턴하는 함수입니다.

아마 기본 함수 선언 내용은 이해하기 어려운 부분은 없으실거에요. 다른 여러 언어들과 약간의 디테일만 다를뿐 큰틀은 동일하기 때문이죠.

리턴값이 없는 함수을 선언할 때는 리턴 타입 선언부에 `Unit`을 써주면 됩니다.

```kotlin
fun printNumber(num: Int): Unit {
	println("this number is $num !!!" )
}
```

사실, 위 함수에서 `Unit` 키워드는 생략해도 무방합니다.

위 코드와 동일 :

```kotlin
fun printNumber(num: Int) {
	println("this number is $num !!!" )
}
```

<br>

코틀린의 함수는 **Default Arguments**와 **Named Arguments**를 지원합니다.

Default Arguments는 매개변수(parameters)에 대응되는 실행인자(arguments)가 없을 때, 매개변수에 자동으로 디폴트 값을 세팅하여 주는 것을 말합니다.

Named Arguments는 함수 호출 시 실행인자에 대응되는 파라미터명을 명시적으로 써주는 방식을 말합니다.

이 두가지 함수선언 방법을 이용하면 가변적인 인자를 필요로 하는 함수를 편리하고 쉽게 작성할 수 있으며 또한 가독성 있고 이해하기 쉬운 코드를 작성할 수 있습니다.

<br>

_예를들어 곡명과 아티스트명을 입력받아서 노래를 재생하는 함수를 만들어 보겠습니다._

_추가적인 요구사항으로 재생모드와 볼륨을 입력 할 수 있는데 이는 선택적으로 입력해도 되고 안해도 됩니다. 하지만 입력값이 없을 때에는 자동으로 재생모드는 normal, 볼륨 크기는 10으로 세팅되도록 하고 싶습니다._



```kotlin
//Default Arguments
fun playMusic(musicName: String,
		artist: String,
		playMode: = "normal",
		volume: Int = 10 ){
...
}

playMusic("윤종신", "좋니") // 재생모드와 볼륨이 디폴트값인 normal과 10으로 세팅됨

playMusic("아이유", "밤편지", "ballad", 15)

//Named Arguments
playMusic(musicName = "가시나",
          artist = "선미",
          playMode = "dance"
)

```
