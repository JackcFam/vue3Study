<template>
    <div>
        <h1 class="text-4xl">Demo Slot</h1>
        <hr>
        <slot :text="slotData" :count="count" :number="100"></slot>
        <header>
            <slot name="header" :nameSlotProps="'xin chào việt nam đây là header'"></slot>
        </header>
        <main>
            <section class="one">
                <slot name="one"></slot>
            </section>
            
            <section class="two">
                <slot name="two"></slot>
            </section>
        </main>
        <footer>
            <slot name="footer"></slot>
        </footer>
    </div>
</template>

<script>
import { ref } from 'vue'
export default {
    setup() {
        const slotData = ref('slotData')
        const count = ref(0)
        return {
            slotData,
            count
        }
    }
}
</script>

<style lang="scss" scoped></style>