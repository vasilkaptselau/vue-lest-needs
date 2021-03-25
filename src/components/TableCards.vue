<template>
<div class="container">
  <div class="row">
    <div class="col-4 offset-4">
      <h1 class="mt-5 mb-4">My Needs List</h1>
      <form @submit.prevent="addNewNeeds" class="border border-primary rounded-bottom shadow p-3 mb-5 bg-white rounded">
        <div class="form-group">
    <label for="exampleInputEmail1">Create a new one</label>
    <input  v-model="newPoint" class="form-control" id="exampleInputEmail1" placeholder="Please types">
  </div>
  <button type="submit" class="btn btn-primary btn-block" :disabled="!newPoint">Submit</button>
        </form>
    </div>
  </div>
  <div class="row mb-2">
  <div class="col-4  mb-4" v-for="(item, index) in newList" :key="item.id">
    <div class="card bg-primary shadow p-3 mb-2 rounded">
      <div class="card-body" @click="toggleDone(item)">
        <h5 class="card-title">{{item.id}}</h5>
        <p class="card-text">{{item.content}}</p>
       <img 
       :class="{done: item.done}" src="../assets/check.png" alt="">
        <button class="btn btn-danger shadow-lg remove" @click="removeItem(index)">X</button>
      </div>
    </div>
      
    </div>
  </div>
</div>
 
</template>

<script>

import { ref } from 'vue'

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  setup(){
    const newPoint = ref('');
    const newList = ref([]);

    function addNewNeeds(){
      newList.value.push({
        id:new Date().toJSON().slice(0,10),
        done:false,
        content: newPoint.value,
        
      });
      newPoint.value = '';
    }
    function toggleDone(item) {
      item.done =!item.done
    }
    function removeItem(index){
newList.value.splice(index, 1)
    }
    return {
      newList,
      newPoint,
      addNewNeeds,
      toggleDone,
      removeItem
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Dela+Gothic+One&display=swap');
h1, label, button{
  font-family: 'Dela Gothic One', cursive;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.card{
  cursor: pointer;
  height: 40vh;
}
img{
  position: absolute;
  top: -40px;
  right: 0px;
  visibility: hidden;
  width: 100px;
}
.done{
visibility: visible;
}
.remove{
position: absolute;
  bottom: 0px;
  right: 0px;
}
</style>
