<template>
  <div class="endpoint">
    <h3 @click="$emit('remove-item', index)">x</h3>
    <h2>{{main.thisname }}</h2>
    <h4>${{ main.thisincome }}</h4>
    <h4>{{ main.thisdate }}</h4>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';

const mainvalue = defineProps({
  main: Object,
  index:Number
})
</script>

<style scoped>
.endpoint{
  display: flex;
  align-items: center;
  width:70%;
  margin:0 auto 10px;
  background-color: white;
  border-radius:10px;
  padding:10px;
  justify-content: space-between;
  color:#777;
  position: relative;
}
.endpoint h3{
  color:indianred;
  font-size: 18px;
  cursor: pointer;
  margin-right: 15px;
  font-weight: bold;
}
.endpoint h2{
  flex:1;
}
.endpoint h4{
  margin-left: 30px;
  font-size: 20px;
}
@media (max-width:550px) {
  .endpoint{
    width:90%;
  }
  .endpoint h3{
    position: absolute;
    top:0;
    right:0;
    transform: translate(50%,-50%);
    margin-right:0;
    background-color: #e2e2e2;
    border-radius: 50%;
    z-index: 10;
    width:30px;
    height:30px;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .endpoint h2{
    font-size: 18px;
  }
  .endpoint h4{
    font-size: 16px;
    margin-left: 15px;
  }
}
</style>