타이포라가 안ㄷ

# 타입스크립트 최대 장점?

반환타입을 명확하게 사용하는 js

# Vue 설치 문제

```powershell
PS C:\tsc> get-executionpolicy
Restricted
PS C:\tsc> set-executionpolicy remotesigned
PS C:\tsc> get-executionpolicy
RemoteSigned
PS C:\tsc> vue create vue-cli
?  Your connection to the default npm registry seems to be slow. 
   Use https://registry.npmmirror.com for faster installation? No   
 vue create vue-cli  이게 vue-cli라는 이름의 프로젝트 생
```

"eslint": "^7.32.0",

vue3 으로 일단 만듬

설정파일은 별도 분리가 확장성있게 관리가능 

# Vue

> 왜 클래스 타입은 권장하지 않는가 
> 
> sutup()이라는 옵션이 실제 프젝에서 vue3에서는 인스턴스 속성 
> 
> vue의 정체성 훼손 문법??...?????????

--fix 나왔던 에러

`npm run lint -- --fix`

v-model 은 반응이 늦어서 props를 사용해서 즉각적으로 해주면 더 좋음

computed:{}  함수 : 타입 // 을 무조건 넣어줘야함 

### computed?

클래스 바인드 등 길어지는 일부 명령어를 함수 형태로 선언해서 사용가능 하게 해주는

storage에 있는 api조회 다시보자

props는 하다보니 대강 알아서 괜춘할듯?

상/하위 컴포넌트 통신은 안다고 할수있지

# 2번째 프로젝트

기존 구현된 서비스에 ts점진적 적용

```
github.com/joshua1988/vue-advanced # 강의코 깃헙 레포
```

플러그인? @vue/cli-plugin-typescript

`vue add typescripte`

js->ts 변경시 문제점

App.vue나 main.ts 가 변경시 덮어씌어지면서 코드가 수정될수있음

버전에 따라 라이브러리 호환성이 다를수있음

`그래서 상황따라 플러그인 자제??`
