<script>
export default {
    data:function (){
        return{
            newTodoItem:'',
                }
    },
    methods:{
        addTodo : function (){
            //로컬스토리지에 저장 - mdn에서 window.localStorage 검색
            //로컬스토리 확인법 : Application 탭에서 Storage
            // ? - 왜 로컬스토리지에 중복값은 저장이 안되지? a: 값이 아니라 키가 중복이 안되는 것이었음.
            let obj = {
                completed:false,
                item: this.newTodoItem
            }
            let txt=this.newTodoItem
            if(txt.replace(/\s/gi,'').length > 0)
            localStorage.setItem(this.newTodoItem,JSON.stringify(obj)); //(키,벨류)
            // 키가 newTodoItem 설정되어있음.
            this.clearInput();
        },
        clearInput:function (){
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