<template>
  <ProductList />
  <hr class="mt-[100px]">
  <DemoSlot>
    <template #header="slotsHeader">
      <div>
        <h2 class="text-red-700">Đây là header {{ slotsHeader.nameSlotProps }}</h2>
      </div>
    </template>
    <template #one>
      <div>
        Đây là section 1
      </div>
    </template>
    <template #two>
      <div>
        Đây là section 2
      </div>
    </template>
    <template #default>
      <div>
        Đây là default
      </div>
    </template>
  </DemoSlot>
  <DemoSlot v-slot="{ text, count, number }">
    {{ text }} and {{ count }} and {{ number }}
  </DemoSlot>
  <DemoDynamicComponent></DemoDynamicComponent>
  <div class="container mx-auto">
    <button @click="open = true">Open Teleport Modal</button>
    <teleport to='body'>
      <TeleportBaseModal v-if="open" class="modal bg-slate-50 min-h-[250px] rounded-lg p-4" @close-modal="handleCloseModal"></TeleportBaseModal>
    </teleport>
    
  </div>
</template>

<script>
import TeleportBaseModal from "./components/TeleportBaseModal.vue";
import ProductList from "@/components/ProductList.vue";
import DemoSlot from "./components/DemoSlot.vue";
import { provide, ref } from 'vue';
import DemoDynamicComponent from "./components/DemoDynamicComponent.vue";
export default {
  components: {
    ProductList,
    DemoSlot,
    DemoDynamicComponent,
    TeleportBaseModal
  },
  setup() {
    const open = ref(false)
    const nameShop = ref('DemoShop')
    provide('NAME', nameShop)
    const handleCloseModal = (value) => {
      open.value = value
    }
    return {
      open,
      nameShop,
      handleCloseModal
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.modal {
  position: fixed;
  z-index: 999;
  top: 20%;
  left: 50%;
  width: 300px;
  margin-left: -150px;
}
</style>
