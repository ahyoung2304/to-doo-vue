<script>
export default {
    data:function (){
        return{
            newTodoItem:'',
                }
    },
    methods:{
        addTodo:function (){
            //로컬스토리지에 저장 - mdn에서 window.localStorage 검색
            //로컬스토리 확인법 : Application 탭에서 Storage
            // ? - 왜 로컬스토리지에 중복값은 저장이 안되지?
            localStorage.setItem(this.newTodoItem,this.newTodoItem); //(키,벨류)
            this.clearInpu();
        },
        clearInpu:function (){
            this.newTodoItem=''
        }
    }
}
</script>

<template>
<div>
    <!--v-model : input 값을 뷰 인스턴스에 동적으로 연결-->
    <input type="text" v-model="newTodoItem" @keyup.enter="addTodo">
    <button v-on:click="addTodo">add</button>
    <span>

    </span>
</div>
</template>

<style scoped>

</style>