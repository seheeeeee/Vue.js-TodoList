<template>
  <div class="inputBox shadow">
      <input type="text" v-model="newTodoItem" placeholder="Type what you have to do" v-on:keyup.enter="addTodo">
      <span class="addContainer" v-on:click="addTodo">
          <i class="addBtn fa fa-plus"></i>
      </span>
  </div>
</template>

<script>
export default {
    data: function(){
        return {
            newTodoItem: ''
        }
    },
    methods: {
        addTodo(){
            if(this.newTodoItem !== ""){//인풋 박스의 입력 값이 있을 때만 저장
                var value = this.newTodoItem && this.newTodoItem.trim();//안풋 박스에 입력된 텍스트의 앞뒤 공백 문자열 제거
                this.$emit('addTodo', value);
                this.clearInput();//인풋 박스의 입력 값을 초기화
            }
        },
        clearInput(){
            this.newTodoItem = '';
        }
    }
}
</script>

<style scoped>
    input:focus{
        outline: none;
    }
    .inputBox{
        background-color: #fff;
        height: 50px;
        line-height: 50px;
        border-radius: 5px;
    }
    .inputBox input{
        border-style: none;
        font-size: 0.9rem;
    }
    .addContainer{
        display: block;
        width: 3rem;
        float: right;
        background: linear-gradient(to right, #6478fb, #8763fb);
        border-radius: 0 5px 5px 0;
    }
    .addBtn{
        color: #fff;
        vertical-align: middle;
    }
</style>