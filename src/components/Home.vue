<template>
    <div>
        <h1>{{ msg }}</h1>
        <h3>Clique no botão para incrementar o contador:</h3>
        <button @click="increment">
            Contador: {{ counter }}
        </button>
    </div>    
</template>

<script setup>
import { useMainStore } from '../stores/main'
import { storeToRefs } from "pinia";
import { mapActions } from 'pinia'
import { ref } from 'vue';

defineProps({
  msg: {
    type: String,
    required: true
  }
})



const main = useMainStore()

const { counter } = storeToRefs(main)

const { increment } = mapActions(useMainStore, ["increment"])
</script>

<style scoped>
button {
  background: linear-gradient(to right, #00c261, #003f1f);
  border: none;
  border-radius: 5px;
  color: white;
  cursor: pointer;
  font-size: 16px;
  padding: 15px 30px;
  transition: all 0.3s;
  margin-top: 16px;
}

button:hover {
  transform: translateY(-2px);
  box-shadow: 0px 5px 10px rgba(0,0,0,0.2);
}
</style>