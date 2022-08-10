<template>
  <div>
    <label for="todo-input">오늘 할 일 : </label>
    <input :value="items" id="todo-input" type="text" @input="handle" />
    <button type="button" @click="addtodo">add</button>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
export default Vue.extend({
  props: {
    items: {
      type: String, 
      required: true, // 무조건 내려와 줘야 하기 때문에 required:true
    },
  },
  methods: {
    handle(event: InputEvent) {
      // Object is possibly 'null' 해결
      // if(!event.target){
      //   return;
      // }
      const eventTarget = event.target as HTMLInputElement;

      eventTarget.value;
      this.$emit("input", eventTarget.value); //input 해당 input은 컴포넌트에 대한 소통
      console.log(eventTarget.value);
      // event.target.value;
      // this.$emit("input", event.target.value); //input 해당 input은 컴포넌트에 대한 소통
      // console.log(event.target.value);
    },
    addtodo() {
      // console.log("sadfaef");
      this.$emit("aadd");
    },
  },
});
</script>

<style scoped></style>
