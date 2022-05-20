<script lang="ts" setup>
import { watch } from 'vue';
import { useKey } from '../composables/useKey';

interface Props {
   visible: boolean;
}
interface Emits {
   (e: 'update:visible', v: boolean): void;
}
const emit = defineEmits<Emits>();
const props = defineProps<Props>();

useKey(
   'esc,command+enter',
   () => {
      console.log('ESC yes');
      emit('update:visible', false);
   },
   { input: true, prevent: true, stop: true, repeat: false, source: () => props.visible },
);

</script>

<template>
   <Teleport to="body">
      <div v-if="props.visible" class="modal-bg">
         <div class="modal-fg">
            <slot />
         </div>
      </div>
   </Teleport>
</template>

<style lang="scss" scoped>
.modal-bg {
   width: 100%;
   height: 100%;
   position: fixed;
   display: flex;
   left: 0;
   top: 0;
   background-color: rgba(22, 22, 22, 0.294);
   padding: 10px;
   align-items: center;
   justify-content: center;

   .modal-fg {
      width: 100%;
      max-width: 600px;
      height: 100%;
      max-height: 400px;
      background-color: white;
      overflow: hidden;
      border-radius: 10px;
      padding: 15px;
      font-family: Arial, Helvetica, sans-serif;
   }
}
</style>
