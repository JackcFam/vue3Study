<template>
  <ProductList/>
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
  <DemoSlot v-slot="{text, count, number}">
    {{ text }} and {{count}} and {{ number }}
  </DemoSlot>
</template>

<script>
import ProductList from "@/components/ProductList.vue";
import DemoSlot from "./components/DemoSlot.vue";
import { provide, ref } from 'vue';

export default {
  components: {
    ProductList,
    DemoSlot
  },
  setup() {
    const nameShop = ref('DemoShop')
    provide('NAME',nameShop)
    return {}
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
</style>
