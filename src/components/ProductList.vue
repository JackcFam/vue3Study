<template>
  <div class="container mx-auto">
    <div class="flex items-center justify-end cursor-pointer">
      <img class="w-10 h-10" src="https://www.svgrepo.com/show/80543/shopping-cart-outline.svg" alt="">
      <p class="font-bold">Cart</p>
    </div>
    <h1 class="text-orange-600 font-semibold text-2xl underline mb-5">
      Danh sách sản phẩm
    </h1>
    <div v-if="productList.length > 0" class="grid grid-cols-4 gap-5">
      <ProductItem @buy="handleBuyNow" v-for="(item, index) in productList" :key="index" :product-item="item" />
    </div>
  </div>
  <input type="text" v-model="textChange" />
</template>
<script setup>
import ProductItem from '@/components/ProductItem.vue'
import { onMounted, ref } from "vue";

let textChange = ref("");
onMounted(() => {
  console.log("Danh sách sản phẩm");
});
function handleBuyNow(value) {
  console.log('nhat', value);
}
const productList = ref([
  {
    name: 'Bàn Phím Bluetooth Logitech K380 - Hàng Chính Hãng',
    price: 595000,
    url: 'https://salt.tikicdn.com/cache/w1200/media/catalog/product/l/o/logitechk380%20bl_1.u425.d20160428.t131922.jpg'
  },
  {
    name: 'Bộ lau nhà xoay 360 độ Sunhouse KS-CL330S',
    price: 282000,
    url: 'https://salt.tikicdn.com/cache/750x750/ts/product/14/12/8b/0eb0574fb727ad1b0e3f403cd3df9ec9.png.webp'
  },
  {
    name: 'Thùng Bia Tiger 24 Lon (330ml / Lon)',
    price: 375000,
    url: 'https://salt.tikicdn.com/cache/750x750/ts/product/6c/81/6f/0c95e4db25d2e119b132bfdaa6170246.png.webp'
  },
  {
    name: 'Tai Nghe Nhét Tai Sony Fontopia MDR-E9LP - Hàng Chính Hãng',
    price: 124000,
    url: 'https://salt.tikicdn.com/cache/750x750/media/catalog/product/_/e/_en-1.u2769.d20170407.t140833.654550.jpg.webp'
  },
  {
    name: 'Apple iPad 10.2-inch (9th Gen) Wi-Fi, 2021',
    price: 6900000,
    url: 'https://salt.tikicdn.com/cache/750x750/ts/product/54/ff/25/bfdf0febe11a28eaa7cd3fa735a82c49.png.webp'
  }
]);
</script>
<style></style>