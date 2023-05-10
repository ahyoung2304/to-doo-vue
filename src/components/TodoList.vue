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
          console.log("=====" + todoItem)
            localStorage.removeItem(todoItem);
          this.todoItems.splice(index,1)//삭제 후 새로운 배열 반환
                                                  //slice 는 삭제 후 기존 배열 반환?
        },
        toggleComplete(){

        }
    },
//라이프사이클 :  생성 > 마운트 > 업데이트 > 디스토..? / 비포마운트 등 포함 총 10개 정도.
   // created :  instance 생성된 후
    created() {
        //localStorage 에 데이터가 있다면
        if(localStorage.length > 0){
            for (var i=0;i<localStorage.length;i++){
                if (localStorage.key(i)!=='loglevel:webpack-dev-server')
               // this.todoItems.push( typeof localStorage.getItem(localStorage.key(i)))
               //      this.todoItems.push( JSON.parse( localStorage.getItem(localStorage.key(i))).item)
                    this.todoItems.push( JSON.parse( localStorage.getItem(localStorage.key(i))))
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
            <input type="checkbox" v-model="todoItem.completed" v-on:click="toggleComplete" >
            <label>{{todoItem.completed? 'checked':'not checked'}}</label>
            <span v-bind:class="{textCompleted:todoItem.completed}">{{todoItem.item}}</span>
            <button @click="removeTodo(todoItem.item,index)">x</button>
        </li>
    </ul>
</div>

<!--    <label> ?-->
<!--        <label>은 HTML에서 입력 양식과 연결된 텍스트를 나타내는 태그입니다. 일반적으로 라디오 버튼, 체크 박스, 드롭다운 등과 함께 사용되며 해당 입력 양식과 관련된 설명 또는 라벨링 역할을 합니다. 위 코드에서는 체크 박스와 연결된 텍스트를 나타내는 데 사용되고 있습니다.-->

    <!--    :class(v-bind:class의 줄임말)-->
<!--    <div :class="{ active: isActive }"></div>-->
<!--    위의 구문은 isActive 데이터 속성의 truthiness에 의해 active 클래스의 존재 여부가 결정됨을 의미합니다.-->
</template>

<style >

.textCompleted{
    color: aqua;
}
</style>