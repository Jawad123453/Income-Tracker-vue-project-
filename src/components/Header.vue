<template>
  <div class="header">
    <h1>Income Tracker</h1>
    <p>${{ finalprice }}</p>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';

const pricing = defineProps({
  finalprice: Number,
})

</script>

<style scoped>
.header{
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding:20px 30px;
  background-color: rgb(78, 70, 70);
  position: relative;
}
.header::after{
  content: "";
  width:100%;
  height:7px;
  bottom:0;
  left:0;
  background-color: gold;
  position: absolute;
}
.header h1{
  color:white;
  font-size: 30px;
}
.header p{
  padding:10px;
  color:white;
  background-color: gold;
  min-width: 100px;
  border-radius: 20px;
  font-weight: bold;
  display: flex;
  align-items:center;
  justify-content: center;
  font-size: 22px;
}
@media (max-width:450px) {
  .header h1{
    font-size: 20px;
  }
  .header p{
    font-size: 18px;
    min-width: 80px;
  }
}
</style>