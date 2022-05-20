<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import { ref } from 'vue';
import HelloWorld from './components/HelloWorld.vue';
import Modal from './components/Modal.vue';

const modalVisible = ref(false);
const modalVisible2 = ref(false);
</script>

<template>
   <button @click="modalVisible = true">Modal Aç</button>
   <Modal v-model:visible="modalVisible">
      <div>Merhabalar ben modal</div>
      <button @click="modalVisible2 = true">Modal Aç 2</button>
   </Modal>
   <Modal v-model:visible="modalVisible2">
      <div>Merhabalar ben modal</div>
      <p>Bana tıklama</p>
   </Modal>
</template>

<style>
#app {
   font-family: Avenir, Helvetica, Arial, sans-serif;
   -webkit-font-smoothing: antialiased;
   -moz-osx-font-smoothing: grayscale;
   text-align: center;
   color: #2c3e50;
   margin-top: 60px;
}
</style>
