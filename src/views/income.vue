<template>
    <div>
        <h1 class="page-title">資產</h1>
        <div class="income">
            <div class="card">
                <div class="card-title">
                    <span>總資產: </span>
                    <span>${{ moneyFormatter(99999) }}</span>
                </div>
                <div class="card-title">
                    <span>本日固定收入:</span>
                    <span style="color: green;">+${{ moneyFormatter(100) }}</span>
                </div>
                <div class="card-title">
                    <span>RSQ評級: </span>
                    <span style="color: green;">優異</span>
                </div>
            </div>
            <div class="card">
                <div id="distribute" style="width: 100%;height:200px;"></div>
            </div>
            <div class="card">
                <div id="score" style="width: 100%;height:200px;"></div>
            </div>
            <div class="card">
                <div id="income" style="width: 100%;height:300px;"></div>
            </div>
        </div>
    </div>
</template>
<script setup>
import * as echarts from 'echarts';
import { onMounted } from 'vue';
import { moneyFormatter } from '../utils'

const distributeOption = {
    grid: {
        left: '2%',
        right: '2%',
        top: '2%',
        bottom: '2%',
    },
    title: {
        text: '資產分配',
        left: 'center'
    },
    tooltip: { trigger: 'item' },
    legend: { show: false },
    series: [
        {
            name: 'Access From',
            type: 'pie',
            radius: ['40%', '80%'],
            avoidLabelOverlap: false,
            label: {
                show: false,
                position: 'center'
            },
            emphasis: {
                label: {
                    show: true,
                    fontSize: 40,
                    fontWeight: 'bold'
                }
            },
            labelLine: {
                show: false
            },
            data: [
                { value: 1048, name: 'Search Engine' },
                { value: 735, name: 'Direct' },
                { value: 580, name: 'Email' },
                { value: 484, name: 'Union Ads' },
                { value: 300, name: 'Video Ads' }
            ]
        }
    ]
};

const incomeOption = {
    title: {
        text: '歷史收益',
        left: 'center'
    },
    grid: {
        left: '3%',
        right: '4%',
        bottom: '3%',
        containLabel: true
    },
    xAxis: [
        {
            type: 'category',
            data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
            axisTick: {
                alignWithLabel: true
            }
        }
    ],
    yAxis: [
        {
            type: 'value'
        }
    ],
    series: [
        {
            name: 'Direct',
            type: 'bar',
            barWidth: '60%',
            data: [200, 180, 200, 202, 201, 210, 220]
        }
    ]
};

const scoreOption = {
    title: {
        text: '資產配置評分',
        left: 'center'
    },
    series: [
        {
            color:['#95cc7a'],
            type: 'gauge',
            startAngle: 90,
            endAngle: -270,
            pointer: {
                show: false
            },
            progress: {
                show: true,
                overlap: false,
                roundCap: true,
                clip: false,

            },
            axisLine: {
                lineStyle: {
                    width: 10
                }
            },
            splitLine: {
                show: false,
                distance: 0,
                length: 10
            },
            axisTick: {
                show: false
            },
            axisLabel: {
                show: false,
                distance: 50
            },
            data: [{
                value: 90,
                name: 'Perfect',
                title: {
                    show:false
                },
                detail: {
                    valueAnimation: true,
                    offsetCenter: ['0%', '-10%']
                }
            },],
            title: {
                fontSize: 14
            },
            detail: {
                width: 50,
                height: 20,
                fontSize: 14,
                color: 'inherit',
                borderColor: 'inherit',
                borderRadius: 20,
                borderWidth: 1,
                formatter: '{value}分'
            }
        }
    ]
};
onMounted(() => {
    echarts.init(document.getElementById('distribute')).setOption(distributeOption);
    echarts.init(document.getElementById('income')).setOption(incomeOption);
    echarts.init(document.getElementById('score')).setOption(scoreOption);
})
</script>
<style scoped>
.income {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
}

.card {
    padding: 0.5rem;
    border-radius: 20px;
    background-color: #fff;
    display: flex;
    justify-content: center;
    align-items: center;
}

.card-title {
    padding: 0 1em;
    box-sizing: border-box;
    width: 100%;
    display: flex;
    justify-content: space-between;
}

.card:nth-child(1) {
    grid-column: 1 / -1;
    justify-content: flex-start;
    align-items: flex-start;
    flex-direction: column;
    text-align: start;
}

.card:nth-child(4) {
    grid-column: 1 / -1;
}
</style>