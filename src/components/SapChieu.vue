<template>
    <div>
        <h1>Sắp chiếu</h1>
        <form action="#" @submit.prevent="handleSearch()" class="flex items-center gap-2 justify-center">
            <label for="search">Tìm kiếm</label>
            <input type="text" v-model="keyword" class="border border-solid focus:ring-transparent focus:outline-none rounded-lg p-2">
            <button class="text-white bg-red-600 hover:bg-red-700 p-2 rounded-lg">Search</button>
        </form>
    </div>
</template>

<script>
import { ref } from 'vue'
export default {
    setup () {
        const keyword = ref('')
        function handleSearch() {
            console.log('Search');
        }

        return {
            keyword,
            handleSearch
        }
    }
}
</script>

<style lang="scss" scoped>

</style>