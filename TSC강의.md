# TSC

## 인풋 컴포넌트 생성 및 등록 컴포넌트 분리

> vue 에서 컴포넌트? -> 기본 HTML 엘리먼트를 확장하여 재사용 가능한 코드를 캡슐화함 경우에 따라 특정 동작이 추가된 엘리먼트로 만들 수 있다?script

```typescript
components 폴더 및에 name.vue 라는 파일로 만듬 파일내에 
ts + tab 으로 기본 vue 화면 만들고 간단한 코드 써줌 이후 
App.vue에서 써줬던 컴포넌트 써주고 <script lang="ts"> 에서 import 해서 사용
 가능 한듯 

// (컴포넌트 부분 Todoinput.vue)
<template>
    <div>
        <label for ='todi_inpurt'></label>
        <input id='todi_input' type = 'text'/>
        <button @click='addTodo' type='button'>add</button>
    </div>
</template>

<script lang='ts'>
import Vue form "vue";
export default Vue.extend({
    methods:{
        addTdo(){
            alert('함수 실행시 나올 내용 ')
        }
    }
})
</script>


++ 그 이후 App.vue 에서 template 부분에  선언한 컴포넌트 <Todoinput> 하면 그대로
쓸 수 있음 일종에 헤더파일?을 만드는 느낌 
```

```typescript
App.vue 부분 
<template>
    <div>
        <h1>vue </h1>
        <TodoInput></TodoInput>
    </div>
</template>

<script lang='ts'>
import Vue form "vue";
import Todoinput from "Todoinput의 경로"
export default Vue.extend({
    components:{TodoInput},
    data(){
        return{
            todoText: ""   # todoText를 TodoInput 컴포넌트에 내릴거임 
        }
    }
})
</script>
```

## 인풋 컴포넌트에 내려줄 data와 props속성

> - data? 해당 컴포넌트나 정의된 method에서 사용가능한 데이터?변수?
> 
> - Props? 컴포넌트가 상위 참조가 안되서 상위에서 하위로 보내기위한 데이터? 옵션?

```typescript
// (컴포넌트 부분 Todoinput.vue)
<template>
    <div>
        <label for ='todi_inpurt'></label>
        <input id='todi_input' type = 'text'/>
        <button @click='addTodo' type='button'>add</button>
    </div>
</template>

<script lang='ts'>
import Vue form "vue";
export default Vue.extend({
    props:["item"],   # 해당 컴포넌트에서 item이라는 데이터를 받을 준비
    methods:{
        addTdo(){
            alert('함수 실행시 나올 내용 ')
        }
    }
})
</script>
```

```typescript
App.vue 부분 
<template>
    <div>
        <h1>vue </h1>
        <TodoInput :item="todoText"></TodoInput>  # item이라는 props속성 가져오기 가능
    </div>              # item이라는 props에 위쪽에 있는 데이터가 내려가는 구조 
</template>

<script lang='ts'>
import Vue form "vue";
import Todoinput from "Todoinput의 경로"
export default Vue.extend({
    components:{TodoInput},
    data(){
        return{
            todoText: ""   # todoText를 TodoInput 컴포넌트에 내릴거임 
        }
    }
})
</script>
```

이후

```typescript
// (컴포넌트 부분 Todoinput.vue)
<template>
    <div>
        <label for ='todi_inpurt'></label>
        <input id='todi_input' type = 'text' :value='item'/>
        <button @click='addTodo' type='button'>add</button>
    </div>    # props는 :콜론으로 시작? 암튼 props를 컴포넌트에서 쓸수있음
</template>

<script lang='ts'>
import Vue form "vue";
export default Vue.extend({
    props:["item"],   # 해당 컴포넌트에서 item이라는 데이터를 받을 준비
    methods:{
        addTdo(){
            alert('함수 실행시 나올 내용 ')
        }
    }
})
</script>
```

## 인풋 컴포넌트의 emit 이벤트 정의 및 구현

++ 실습 한거를 가져오는게 빠를듯 

methods 함수(event:any)로 해줘야 함 

$emit는 컴포넌트간 대화하기위한 수단 
