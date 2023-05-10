<script >
export default {
    methods:{
        clearAll:function (){
            localStorage.clear()

        }
    }
}

/* 컴포넌트의 성격에 따른 종류
  1. 컨테이너 : 로직을 담고 있음
  2. 프레젠터 : 화면에 보여짐
  ==> 전체 컴포넌트에서 사용하는 데이터를 한 곳에 몰아 놓음. 그곳에서 데이터 조작이 일어남. ( vuex )
 */
</script>

<template>
<div>
    <button @click="clearAll">clear all</button>
</div>
</template>

<style scoped>

</style>