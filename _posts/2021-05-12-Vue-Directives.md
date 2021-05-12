---
title: "Vue.js - Directives"
excerpt: "v- 접두사가 있는 특수 속성을 알아보자 "

categories:
  - Vue
tags:
  - Vue
  - JavaScript
last_modified_at: 2021-05-12 03:13:00
toc: true
toc_sticky: true
---

### 디렉티브 Directives

> 디렉티브는 v- 접두사가 있는 특수속성

> 디렉티브 속성 값은 단일 JacaScript 표현식이 됨 (v-for는 예외)

> 디렉티브의 역할은 표현식의 값이 변경될 때 사이드 이펙트를 반응적으로 DOM에 적용

### v-model

> 양방향 바인딩 처리를 위해서 사용

> - Data binding이란 VueJs의 binding expressions을 사용하여 script와 DOM간의 데이터를 주고받는 과정을 의미

```js
<div id="app">
      <input type="text" v-model="msg" />
      <div v-html="msg"></div>
    </div>
    <script>
      new Vue({
        el: "#app",
        data: {
          msg: "<h2>'Hello Vue~!'</h2>",
        },
      });
    </script>
```

### v-bind

> 엘리먼트의 속성과 바인딩 처리를 위해서 사용\
> v-bind는 약어로 ":" 로 사용 가능.

```js

    <div id="app">
        <!-- 속성을 바인딩. -->
        <div v-bind:id="idValue">v-bind 지정 연습</div>
        <button v-bind:[key]="btnId">버튼</button>

        <!-- 약어를 이용한 바인딩. -->
        <div :id="idValue">v-bind 지정 연습</div>
        <button :[key]="btnId">버튼</button>

        <a v-bind:href="link1">구글</a>
        <a :href="link2">네이버</a>
    </div>
    <script>
        new Vue({
            el: '#app',
            data: {
                idValue: 'test-id',
                key: 'id',
                btnId: 'btn1',
                link1: 'http://www.google.com',
                link2: 'http://www.naver.com'
            }
        });
    </script>
```

### v-show

> 조건에 따라 엘리먼트를 화면에 렌더링.\
> style의 diplay를 변경.

```js
    <div id="app">
      <div v-show="isShow">{{msg}}</div>
    </div>
    <script>
      new Vue({
        el: "#app",
        data: {
          isShow: true,
          msg: "보이나요?",
        },
      });
    </script>
```

### v-if, v-else-if, v-else

> 조건에 따라 엘리먼트를 화면에 렌더링

```js
  <div id="app">
      <div>
        <span>나이 : </span>
        <input type="number" v-model="age" />
      </div>
      <div>
        요금 :
        <span v-if="age < 10">무료</span>
        <span v-else-if="age < 20">7000원</span>
        <span v-else-if="age < 65">10000원</span>
        <span v-else>3000원</span>
      </div>
    </div>
    <script>
      const vm = new Vue({
        el: '#app',
        data: {
          age: '0',
        },
      });
    </script>
```

### v-for

> 배열이나 객체의 반복에 사용\
> v-for="요소변수이름 in 배열"\
> v-for="(요소변수이름,인덱스) in 배열"

```js
   <div id="app">
      <h2>범위지정(4)</h2>
      <span v-for="i in 4"> {{i}} </span>

      <h2>문자열 배열</h2>
      <ul>
        <li v-for="name in regions">{{name}}</li>
      </ul>

      <h2>문자열 배열 - 위치</h2>
      <ul>
        <li v-for="(name, i) in regions">번호 : {{i}}, 지역 : {{name}}</li>
      </ul>
    </div>
    <script>
      new Vue({
        el: "#app",
        data: {
          regions: ["광주", "구미", "대전", "서울"],
        },
      });
    </script>
```

### template

> 여러 개의 태그들을 묶어서 처리해야 할 경우 template 사용.\
> v-if, v-for, component 등과 함께 많이 사용

```js
<template v-if="count % 2 == 0">
  <h4>여러개의 태그를 묶어서 처리해야 한다면??</h4>
  <h4>template 태그를 사용해 보자</h4>
  <h4>만약에 template가 없다면?? 각태그마다 v-if?</h4>
</template>
```

#### Vue method ?

> Vue 인스턴스는 생성과 관련된 data 및 method의 정의 가능\
> method 안에서 data를 "this.데이터이름" 으로 접근 가능

```js
    <div id="app">
      <div>data : {{message}}</div>
      <div>method kor : {{helloKor()}}</div>
      <div>method eng : {{helloEng()}}</div>
    </div>
    <script>
      new Vue({
        el: '#app',
        data: {
          message: 'Hello ~',
          name: '찬',
        },
        methods: {
          helloEng() {
            return 'Hello ' + this.name;
          },
          helloKor() {
            return '안녕 ' + this.name;
          },
        },
      });
    </script>
```
