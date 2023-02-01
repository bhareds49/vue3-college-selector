
<template>
  <div class="hello"> 

    <div> 
      <input class="search" type="text" v-model="input" placeholder="Search Here"/>
    </div>
    
  

    <div class="college-list" v-for="uni in filteredList()">
      <p>{{ uni.name }} ({{ uni.country }})</p>
    </div>

    <div class="item-error" v-if="input&&!filteredList().length">
      <p>No results found!</p>
    </div>
  </div>

</template>

<script setup>
  import uni from "./components/json/uni.json";
  import { ref } from "vue";
  let input = ref("");

  //filter list based on input
  //refactor filtered list to be a function
  //so that it can be called in the template
  //and re-evaluated when input changes
  function filteredList() {
    return uni.filter((uni) => {
      return uni.name.toLowerCase().includes(input.value.toLowerCase());
    });
  }


</script>

<style scoped>

.search {
    width: 100%;
    padding: 24px;
    margin: 8px 0;
    box-sizing: border-box;
    border: 2px solid hsla(160, 100%, 37%, 1);
    border-radius: 15px;
    outline: none;
    font-size: 24px;
  }
  .search:focus {
    border: 2px solid #555;
}
  .college-list {
    background-color: #f1f1f1;
    padding: 8px; 
    padding-left: 24px;
    margin-top: 8px;
    color: black;
    border-radius: 15px;
    font-size: 24px;
    transition: .5s;
  }

  .college-list:hover {
    background-color: hsla(160, 100%, 37%, 1);
    transition: .5s;
  }

  .item-error {
    background-color: #f1f1f1;
    padding: 8px;
    padding-left: 24px;
    margin-top: 8px;
    color: hsla(160, 100%, 37%, 1);
    border-radius: 15px;
    font-size: 24px;
  }



</style>
