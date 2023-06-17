<template>
    <div>
        <h1>Modal</h1>
        <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Delectus expedita sunt consequuntur debitis repudiandae! Quam, eius porro. Deserunt esse nam voluptates harum fugit dignissimos optio dolorem quod. Exercitationem, ipsa nobis.</p>
        <div class="flex items-center justify-end">
            <button @click="$emit('closeModal',open)" class="bg-red-500 text-white p-1 rounded-lg">Close Modal</button>
        </div>
        
    </div>
</template>

<script>
import { ref } from 'vue'
export default {
    emits: ['closeModal'],
    setup () {
        const open = ref(false)
        return {
            open
        }
    }
}
</script>

<style lang="scss" scoped>

</style>