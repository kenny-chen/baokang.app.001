<template>
    <div class="sticky-footer">
        <div class="f-circle" v-for="(item, index) in list" :key="index" 
        :style="{ backgroundColor:index === active ? '#FFF' : '' }"
        @click="pageChange(index)">
            <img :src="index === active ? item.activeImg : item.img" alt="" width="32px">
        </div>
    </div>
</template>
<script setup>
import { ref , defineEmits } from 'vue'
import home from "../assets/home.png"
import insurance from "../assets/insurance.png"
import income from "../assets/income.png"
import profile from "../assets/profile.png"
import homeActive from "../assets/home_a.png"
import insuranceActive from "../assets/insurance_a.png"
import incomeActive from "../assets/income_a.png"
import profileActive from "../assets/profile_a.png"

let active = ref(0)
const list = [
    {
        img:home,
        activeImg:homeActive
    },
    {
        img:insurance,
        activeImg:insuranceActive
    },
    {
        img:income,
        activeImg:incomeActive
    },
    {
        img:profile,
        activeImg:profileActive
    },
]

let emits = defineEmits(['pageChange'])

function pageChange(index){
    active.value = index
    emits('pageChange',index)
}

</script>
<style scoped>
.sticky-footer {
    position: fixed;
    bottom: 20px;
    height: 6vh;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    padding-left: 10px;
}
.f-circle {
    width: 6vh;
    height: 6vh;
    border-radius: 50%;
    background-color: #7F7E7E;
    border: 10px solid #666;
    display: flex;
    justify-content: center;
    align-items: center;
}
.f-circle:nth-child(2) {
    transform: translateX(-10px);
}
.f-circle:nth-child(3) {
    transform: translateX(-20px);
}
.f-circle:nth-child(4) {
    transform: translateX(-30px);
}
</style>