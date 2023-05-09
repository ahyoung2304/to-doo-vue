<script >
import TodoHeader from "@/components/TodoHeader.vue";
import TodoFooter from "@/components/TodoFooter.vue";
import TodoInput from "@/components/TodoInput.vue";
import TodoList from "@/components/TodoList.vue";

// 컴포넌트 등록방법(es5) - sfc가 아닌 cdn으로 스크립트 로딩하는 방식으로 할 때(?) new Vue()를 쓴다?

// var my_cmp={
//     template:'<div>my component</div>'
// };
// new Vue({
//     el:'',
//     components:{
//         //컴포넌트명 : 컴포넌트 내용
//         'my-cmp':my_cmp
//     }
// })


// 컴포넌트 등록 es6?
export default {
    components:{
    // 컴포넌트 태그명 : 컴포넌트 내용
        'TodoHeader':TodoHeader,
        'TodoInput': TodoInput,
        'TodoFooter': TodoFooter,
        'TodoList': TodoList,

    }
}
</script>

<template>
  <div id="app">
      <TodoHeader></TodoHeader>
      <TodoInput ></TodoInput>
      <TodoList></TodoList>
      <TodoFooter></TodoFooter>

  </div>
</template>

<style scoped>


</style>
