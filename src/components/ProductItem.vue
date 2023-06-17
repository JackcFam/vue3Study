<template lang="">
    <div v-if="error"></div>
    <div class="shadow-lg p-4 rounded-lg max-w-sm group cursor-pointer relative">
        <div class="absolute z-50 right-0 top-0 bg-green-600 p-2 rounded-l-lg">
            <p class="text-white">{{ nameShop }}</p>
        </div>
        <img class="w-full h-72 group-hover:animate-pulse" :src="props.productItem.url" alt="">
        <h4 class="text-lg w-full text-left font-normal mt-3">{{ props.productItem.name }}</h4>
        <p class="text-lg font-bold">{{ props.productItem.price.toLocaleString('vi', {style : 'currency', currency : 'VND'}) }}</p>
        <div class="flex justify-between items-center my-2">
            <button @click="handleBuyNow(props.productItem)" class="bg-red-600 hover:bg-red-800 text-white p-2 rounded-lg">Mua Ngay</button>
            <button @click="handleAddToCart(props.productItem)" class="bg-blue-600 hover:bg-blue-800 text-white p-2 rounded-lg">Thêm vào giỏ hàng</button>
        </div>
        <GlobalComponent />
        <button @click="increment()" class="bg-slate-200 p-1 rounded-xl w-full">{{ state.count }} and {{ state.double }} and {{ triple }}</button>
    </div>
</template>
<script setup>
import { computed, inject, onBeforeMount, onErrorCaptured, onMounted, onUnmounted, onUpdated, reactive, ref, useAttrs, watch, watchEffect } from "vue";
const props = defineProps({
    productItem: {
        type: Object,
        required: true
    },
    name: {
        type: String,
        required: false,
        validator(value) {
            if(value.length > 10) {
                return true
            }
            return false
        }
    },
    price: [String, Number],
    img: String
})
const emit = defineEmits(['add','buy']);
console.log(props.productItem)
const attrs = useAttrs();
console.log('attrs', attrs);
let state = reactive({
    count: 0,
    double: computed(() => state.count * 2)
});
const triple = computed(() => {
    return state.count * 3;
});
onBeforeMount(() => {
    console.log('onBeforeMount');
})
onMounted(() => {
    console.log('onMount');
})
onUpdated(()=>{
    console.log('onUpdated');
})
onUnmounted(() => {
    console.log('destroy');
})
watchEffect(() => {
    console.log(state.count);
})
watch(
  () => triple,
  (count) => {
    console.log(count)
  }
)
const increment = () => state.count++;
const error = ref(null);
//provide/inject
const nameShop = inject('NAME')
onErrorCaptured((e) => {
    error.value = e
    return true;
})
function handleBuyNow(product) {
    console.log(product);
    emit('buy',product)
}
</script>
<style lang="">
    
</style>