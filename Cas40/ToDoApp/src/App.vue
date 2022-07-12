<template>
  <div class="container">
    <h1>ToDo App</h1>
    <form action="mysite.php"  @submit.prevent>
      <label for="todo">New ToDo</label>
      <input type="text" id="todo" ref="item">
      <button class="addBtn" @click="addItem">Add ToDo</button>      
    </form>
    <h2>ToDo List</h2>
    <ul>
      <!-- <li v-for="item in list" :key="items" >{{item}}</li> -->
      <ListItem v-for="(item, index) in list" :key="index" :item="item" @removeItem="deleteItem"></ListItem>
    </ul>
  </div>


</template>

<script setup>
  import {ref} from 'vue'
  import ListItem from './components/ListItem.vue';

  let item = ref()
  let list = ref([])
  function addItem(){
    list.value.push(item.value.value) 
    item.value.value = ''   
  }

  function deleteItem(index){
    list.value.splice(index,1)
  }

</script>

<style>

  *{
    box-sizing: border-box;
  }

  .container{
    width: 40%;
    margin: 0 auto;
  }

  h1, h2, label{
    color: #fff;
  }

  h1{
    text-align: center;
  }

  form{
    display: flex;
    flex-direction: column;
    width: 100%;
  }

  label{
    font-size: 14px;
  }

  input{
    height: 45px;
    width: 100%;
    background-color: transparent;
    color: #fff;
    box-shadow: none;
    outline: none;
    font-size: 18px;
    border: 2px solid hsla(0,0%,100%,.35);
    border-radius: 6px;
    padding-left: 12px;
    padding-right: 12px;
    margin-top: 10px;
    margin-bottom: 14px;
  }

  h2{
    border-bottom: 2px solid hsla(0,0%,100%,.35);
  }

  .addBtn{
    background-color: #a0a4d9;
    border: 1px solid #a0a4d9;
    border-radius: 6px;
    color: #1f2023;
    width: 100%;
    box-shadow: none;
    outline: none;
    font-size: 18px;
    height: 48px;
    padding-left: 12px;
    padding-right: 12px;
    margin-top: 6px;
    margin-bottom: 12px;
    cursor: pointer;
  }

  ul{
    list-style-type: none;
    padding-left: 0;
  }
</style>
