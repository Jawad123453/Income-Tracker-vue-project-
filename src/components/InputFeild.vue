<template>
  <div class="maininput">
    <div class="centeringthing">
      <input type="text"  placeholder="Income Description" :value="Namevalue" @input="$emit('save-value', $event.target.value)" required>
      <input type="number" min="0" placeholder="Income Value" :value="Icomevalue" @input="$emit('save-numbervalue', $event.target.value)" required>
      <input type="date" :value="Datavalue" @input="$emit('save-Datevalue', $event.target.value)" required>
    </div>
    <button @click="$emit('main-submite')">SUBMIT</button>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';

const propData = defineProps({
  Namevalue: String,
  Icomevalue:String,
  Datavalue: String
})
</script>

<style scoped>
.maininput{
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 80%;
  margin:20px auto;
}
.centeringthing{
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex:1;
  width:100%;
}
.maininput input{
  flex:1;
  padding:10px 15px;
  outline: none;
  border: none;
  font-size: 22px;
}
.maininput input:nth-child(1){
  border-top-left-radius: 20px;
  border-bottom-left-radius: 20px;
}
.maininput button{
  color:white;
  padding:10px 20px;
  background-color: gold;
  border: none;
  font-size: 22px;
  outline: none;
  font-weight: bold;
  border-top-right-radius: 20px;
  border-bottom-right-radius: 20px;
  cursor: pointer;
  transition: 0.3s ease;
}
.maininput button:hover{
  transform: scale(1.2);
}
@media (max-width:1200px) {
  .maininput{
    flex-direction: column;
  }
  .maininput button{
    border-radius: 20px;
    width:100%;
    margin-top: 15px;
  }
  .maininput button:hover{
    transform: scale(1.1);
  }
  .maininput input:nth-child(3){
    border-top-right-radius: 20px;
    border-bottom-right-radius: 20px;
  }
}
@media (max-width:1000px) {
  .centeringthing{
    flex-direction: column;
    gap:15px;
  }
  .centeringthing input{
    border-radius: 20px;
    width:100%;
  }
}
</style>