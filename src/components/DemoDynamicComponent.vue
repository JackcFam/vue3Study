<template>
    <div class="container mx-auto pb-10">
        <div class="flex items-center justify-center gap-6">
            <button @click="switchComponent='DangChieu'" class="p-2 bg-red-500 rounded-lg text-white font-bold">
                Đang chiếu
            </button>
            <button @click="switchComponent='SapChieu'" class="p-2 bg-blue-300 rounded-lg text-white font-bold">
                Sắp chiếu
            </button>
        </div>
        <div>
            <!-- <DangChieu v-if="switchComponent"></DangChieu>
            <SapChieu v-else></SapChieu> -->
            <keep-alive>
                <component :is="switchComponent"></component>
            </keep-alive>
            
        </div>
    </div>
</template>

<script>
import SapChieu from "@/components/SapChieu.vue";
import DangChieu from "@/components/DangChieu.vue";
import { ref } from 'vue';
export default {
    components: {
        SapChieu,
        DangChieu
    },
    setup () {
      
        let switchComponent = ref('DangChieu')

        return {
            switchComponent
        }
    }
}
</script>

<style lang="scss" scoped>

</style>