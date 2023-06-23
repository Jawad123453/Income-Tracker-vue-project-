<script setup>
import Header from './components/Header.vue';
import InputFeild from './components/InputFeild.vue';
import reultinput from './components/reultinput.vue';
import { ref } from 'vue';
import { toNumber } from '@vue/shared';

const Namevalue = ref("")
const Icomevalue = ref("")
const Datavalue = ref("")
const fillvalue=ref("")

const finalprice = ref(0)
const removelprice=ref(0)

const mainarray= ref([])


const EntertoArray = () => {
  if (Namevalue.value != "" && Icomevalue.value != "" && Datavalue.value != "") {
    const mainobject = {
      thisname: Namevalue.value,
      thisincome: Icomevalue.value,
      thisdate: Datavalue.value
    }
    mainarray.value.push(mainobject);
    finalprice.value = parseInt(finalprice.value) + parseInt(Icomevalue.value)
    Namevalue.value = ""
    Icomevalue.value = ""
    Datavalue.value = ""
  } else {
    setTimeout(() => {
      fillvalue.value = ""
    }, 2000);
    fillvalue.value = "Enter The Above Values";
  }
}
const removefromarray = (e) => {
  finalprice.value = parseInt(finalprice.value) - parseInt(mainarray._rawValue[e].thisincome)
  mainarray.value = mainarray.value.filter((number, index) => index != e)
}

</script>


<template>
  <main>
    <Header :finalprice="finalprice"/>
    <InputFeild :Namevalue="Namevalue" :Icomevalue="Icomevalue" :Datavalue="Datavalue" @save-value="Namevalue = $event" @save-numbervalue="Icomevalue = $event"
    @save-Datevalue="Datavalue = $event" @main-submite="EntertoArray"/>
    <div class="wrong" v-if="fillvalue != ''">
      <h1>{{ fillvalue }}</h1>
    </div>
    <reultinput v-for="(main,index) in mainarray" :key="index" :main="main" :index="index" @remove-item="removefromarray(index)"/>
  </main>
</template>

<style>
*{
  padding:0;
  margin:0;
  box-sizing: border-box;
  font-family:sans-serif;
}
#app{
  background-color: #e2e2e2;
  width:100%;
  min-height: 100vh;
}
.wrong{
  width:fit-content;
  margin:0 auto 10px;
  font-size: 8px;
  color:red;  
}
</style>
