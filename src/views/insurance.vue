<template>
    <div>
        <h1 class="page-title">醫保</h1>
        <div class="bill">
            <div class="bill-box">
                <div style="color:#989898">醫保餘額</div>
                <div>${{ moneyFormatter(paid) }}</div>
            </div>
            <div class="bill-box">
                <div style="color:#989898">醫保總額</div>
                <div>${{ moneyFormatter(total) }}</div>
            </div>
        </div>
        <div id="main" style="width: 100%;height:50px;"></div>
        <div class="claim-box">
            <div>周邊醫院</div>
            <div class="claim-box-circle">
                <div class="claim-box-text">共17家</div>
            </div>
        </div>
        <div class="claim-type">
            <h2>報銷項目</h2>
            <div class="claim-type-grid">
                <div class="claim-type-card" v-for="(item, index) of claimTypeCard" :key="index">
                    <div class="title">{{ item.title }}</div>
                    <img :src="item.img" alt="" width="100%" class="img">
                </div>
            </div>
        </div>
    </div>
</template>
<script setup>
import * as echarts from 'echarts';
import { onMounted } from 'vue';
import claimDentalImg from '../assets/claim-dental.jpg'
import claimMedicalImg from '../assets/claim-medical.jpg'
import claimSupperImg from '../assets/claim-supper.jpg'
import claimAccidentImg from '../assets/claim-accident.png'
import { moneyFormatter } from '../utils'

const total = 100000
const paid = 32000


const usedClaim = (paid / total) * 100

const step = 2
const gap = 1
const series = []
for (let i = 0; i < usedClaim; i += step) {
    series.push({
        data: [step],
        type: 'bar',
        stack: 'x',
        barWidth: 40,
        color: '#2E59F2',
        itemStyle: {
            borderColor: '#fff',
            borderWidth: 2,
        }
    })
}
const option = {
    grid: {
        left: '2%',
        right: '2%',
        top: '2%',
        bottom: '2%',
    },
    title: {
        show: false,
    },
    tooltip: {},
    legend: {
        show: false,
    },
    xAxis: {
        axisLabel: {
            show: false
        },
        max: 100
    },
    yAxis: {
        show: false,
        data: ['衬衫']
    },
    series: series
};

const claimTypeCard = [
    {
        title: '住院',
        img: claimMedicalImg
    },
    {
        title: '牙科',
        img: claimDentalImg
    },
    {
        title: '意外',
        img: claimAccidentImg
    },
    {
        title: '保健品',
        img: claimSupperImg
    },
    {
        title: 'Dental',
        img: claimDentalImg
    },
    {
        title: 'Dental',
        img: claimDentalImg
    }
]

onMounted(() => {
    const myChart = echarts.init(document.getElementById('main'));
    myChart.setOption(option);
})
</script>
<style scoped>
.title {
    font-size: 1.5rem;
    margin-bottom: 10px;
}
.img{
    border-radius: 15px;
    height: 20vh;
    object-fit: cover;
}

.bill {
    display: flex;
    justify-content: space-between;
}

.bill-box {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
.claim-type-card{
    border-radius: 15px;
    background-color: var(--primary-color-light);
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    overflow: hidden;
}
.claim-type-card .title{
    padding-top: 10px;
    padding-left: 10px;
    font-weight: 600;
    color:#fff;
}
.claim-type-grid{
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 0.5rem;
}
.claim-box{
    margin-top: 0.5rem;
    border-radius: 20px;
    background-color: #fff;
    box-shadow: 1px 1px 2px #ccc;
    padding: 1rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-weight: 600;
    font-size: 1.5rem;
}

</style>