<template>
  <div>
    <header>
      <h1>Vue todo with typescript</h1>
      <main>
        <TodoInput
          :items="todoText"
          @input="updatetodo"
          @add="addtodoitem"
        ></TodoInput>
        <div>
          <ul>
            <TodoList></TodoList>
            <!-- <li>아이템 1</li>
            <li>아이템 2</li>
            <li>아이템 3</li> -->
          </ul>
        </div>
      </main>
    </header>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import TodoInput from "./components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";

const STORAGE_KEY = "vue-todo-ts-v1"
const storage = {  // storage -> localstorage를 가르킴 API구현
  fetch(){
    const todoItem = localStorage.getItem(STORAGE_KEY) || "[]"; // []을 일단 문자로 만들어서 타입에러 해결 // 앞쪽값이 nul이면 빈 문자열 callback함수
    const result = JSON.parse(todoItem);    // 배열 데이터는 json간주로 되고 object로 변환이 됨
    return result;
  },
  save(todoItems: any[]){
    const parsed = JSON.stringify(todoItems)  // 배열받아서 문자열로 바꾸고 그대로 들어감
    localStorage.setItem(STORAGE_KEY,parsed)  // STORAGE_KEY 라는 위치에 저장됨 
  },
}

export default Vue.extend({
  components: { TodoInput, TodoList },
  data() {
    return {
      todoText: "",
      todoItems:[] as any[],  // 타입 정확하게
    };
  },
  methods: {
    updatetodo(value: string) { // 함수 자체의 반환타입 void인데 return을 쓰면 해당으로 반환됨
      this.todoText = value;
      console.log("todotext", this.todoText);
    },
    addtodoitem() {
      const value = this.todoText;
      this.todoItems.push(value);    // push(밀어넣기)
      localStorage.setItem(value, value); // 이벤트 그대로 받기
      this.inittodotext();
    },
    inittodotext() {
      this.todoText = ""; // todoText 초기화
    },
    fetchTodoitems(){
      this.todoItems = storage.fetch();
    }
  },
  created(){
    this.fetchTodoitems();
  }
});
</script>

<style scoped></style>
