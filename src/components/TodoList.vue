<template>
  <section>
      <ul>
        <li class="shadow" v-for="(todoItem, index) in propsdata" v-bind:key="todoItem">
            <i class="checkBtn fa fa-check"></i>
            {{ todoItem }}
            <span class="removeBtn" type="button" v-on:click="removeTodo(todoItem, index)">
                <i class="fa fa-trash-alt"></i>
            </span>
        </li>

      </ul> 
  </section>
</template>

<script>
export default {
    props: ['propsdata'],
    methods: {
        removeTodo(todoItem, index){//index vue for에서 기본으로 제공하는 인덱스 변수
            this.$emit('removeTodo', todoItem, index);
        }
    }
}
</script>

<style scoped>
    ul{
        list-style: none;
        padding-left: 0px;
        margin-top: 0;
        text-align: left;
    }
    li{
        display: flex;
        min-height: 50px;
        height: 50px;
        line-height: 50px;
        margin: 0.5rem 0;
        padding: 0 0.9rem;
        background-color: #fff;
        border-radius: 5px;
        font-weight: 600;
    }
    .checkBtn{
        line-height: 45px;
        color: #62acde;
        margin-right: 10px;
    }
    .removeBtn{
        margin-left: auto;
        color: #de4343;
    }
</style>