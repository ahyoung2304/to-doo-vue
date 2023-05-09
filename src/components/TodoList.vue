<script>
export default {
    //data 를 function()으로 리턴하는 이유가 뭐였지?
    data:function (){
        return{
               todoItems:[],
        }
    },
    methods:{
        removeTodo(todoItem,index){ //todoItem 은 로컬스토리지 삭제에 활용, index 는 데이터의 배열 삭제에 활용
          localStorage.removeItem(todoItem);
          this.todoItems.splice(index,1)//삭제 후 새로운 배열 반환
                                                  //slice 는 삭제 후 기존 배열 반환?
        },
    },
//라이프사이클 :  생성 > 마운트 > 업데이트 > 디스토..? / 비포마운트 등 포함 총 10개 정도.
   // created :  instance 생성된 후
    created() {
        //localStorage 에 데이터가 있다면
        if(localStorage.length > 0){
            for (var i=0;i<localStorage.length;i++){
                if (localStorage.key(i)!=='loglevel:webpack-dev-server')
              this.todoItems.push(localStorage.key(i))
            }
        }
        console.log(this.todoItems)
    }
}
</script>

<template>
<div>
    <!--리스트 개수만큼 뿌리는건 v-for 사용-->
    <ul>
        <li v-for="(todoItem,index) in todoItems">
            <input type="checkbox" v-on:click="">
            {{todoItem}}
            <button @click="removeTodo(todoItem,index)">x</button>
        </li>
    </ul>
</div>
</template>

<style scoped>

</style>