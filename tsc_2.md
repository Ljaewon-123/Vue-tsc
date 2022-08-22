# Error

```typescript
implicitly has on 'any' type
```

점진적 적용을 위해 `tsconfig.json` 

```typescript
"strict": false,     // true로 하면 타입을 적할수 있음  true로 해야 tsc의 특성을 살린
"noImplicitAny":false, // 타입에 any라도 넣어라 라는 ?? true로 해야 tsc의 특성을 살린거?
"allowJs":true,
```

또다른 내용 때문에 해결안됨 

js파일을 인식시키려면  "allowJs"사용 해서 해결이됨 

No type error found 기본적인 에러 해결

`npm run build 시 빌드에 나오는 에러 확인가능 `

App.vue 모든 cp의 최상위 컴포넌트

**store사용할때 안할때?**

```typescript
api를 호출하고 데이터의 스팩을 정의 할때 typescript가 많이 좋다
store 사용 안해도 될때 :
데이터를 불러와서 cp에 한번만 props를 하면되는 데이터구조 일 굳이 store를 쓸필요는 없다 
ㅜ
async await 비동기 처리 async 기본적인 return은 promise임
```

`computed의 반환타입은 꼭 적어줘야함 `

# props의 타입 정의 장점???? axios?

axiosInstance

# 재네릭 & omit 유틸리티 타입

```
https://joshua1988.github.io/ts/guide/generics.html  # 재네릭
https://joshua1988.github.io/ts/usage/utility.html#%EC%9E%90%EC%A3%BC-%EC%82%AC%EC%9A%A9%EB%90%98%EB%8A%94-%EC%9C%A0%ED%8B%B8%EB%A6%AC%ED%8B%B0-%ED%83%80%EC%9E%85-%EB%AA%87-%EA%B0%9C-%EC%95%8C%EC%95%84%EB%B3%B4%EA%B8%B0
```

# state, store? 캡틴판교 Vuex 시작하기

```
https://joshua1988.github.io/web-development/vuejs/vuex-start/#%EC%83%81%ED%83%9C-%EA%B4%80%EB%A6%ACstate-management%EA%B0%80-%EC%99%9C-%ED%95%84%EC%9A%94%ED%95%9C%EA%B0%80
```

```
vue $store.
            .state
            .commit
            .dispatch
            .getters

vue $store mutations , module , getter?
store를 각각 모듈화를 해서 나눠 선언함 
export 에서 export type 변수 = typeof state; # 중요함 
```

# Cracking Vue.js

```
https://joshua1988.github.io/vue-camp/ts/vuex.html#vuex-%E1%84%80%E1%85%B5%E1%84%87%E1%85%A9%E1%86%AB-%E1%84%8F%E1%85%A9%E1%84%83%E1%85%B3
```

state 관한게 일단있음 typescript 쪽에  Vuex

state는 뮤테이션을 사용해서 넘김 

# 타입 2개를 합칠때

```typescript
type A = {
    name: string;
};
type B = {
    age: number;
};
type C = A & B;
const person: C = {
    name: "a",
    age: 10,
};

// 이렇게 해야 제대로된 타입정의 
```

# Omit

타입정의된거에서 특정 키만 빼고 가져가겠다  ex)

```typescript
const person: C = {
    name: "a",
    age: 10,
    skill: "js",
};
const josh = Omit<person, 'skill'>
josh = {
    name: "a",
    age: 10
}
```
