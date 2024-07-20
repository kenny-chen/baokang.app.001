<template>
    <div class="home-page">
        <h1 class="page-title">目標規劃</h1>
        <div class="card">
            <div class="plan-title">被動收入</div>
            <div class="plan-detail">
                <div>(香港)銀色債</div>
                <div>${{ moneyFormatter(300000) }}</div>
                <div>(香港)綠色債</div>
                <div>${{ moneyFormatter(300000) }}</div>
                <div>(香港)中資美元債</div>
                <div>${{ moneyFormatter(300000) }}</div>
                <div>(香港)六個月定期存款</div>
                <div>${{ moneyFormatter(300000) }}</div>
            </div>
        </div>
        <div class="card">
            <div class="plan-title">保險資產</div>
            <div class="plan-detail">
                <div>(上海)城鎮居民醫療保險</div>
                <div>${{ moneyFormatter(100000) }}</div>
                <div>(香港)高端醫療保險</div>
                <div>${{ moneyFormatter(100000) }}</div>
                <div>(香港)香港終生年金</div>
                <div>${{ moneyFormatter(100000) }}</div>
            </div>
        </div>
        <div class="card">
            <div class="plan-title">公共津貼</div>
            <div class="plan-detail">
                <div>(香港)醫療卷</div>
                <div>${{ moneyFormatter(5000) }}</div>
                <div>(香港)生果金</div>
                <div>${{ moneyFormatter(2000) }}</div>
            </div>
        </div>
    </div>
</template>
<script setup>
import { moneyFormatter } from '../utils'
</script>
<style>
.home-page {
    height: 100vh;
}

.card {
    padding: 1em;
    margin-bottom: 1rem;
    border-radius: 15px;
    background-color: #fff;
    box-shadow: 1px 1px 2px #ccc;
}

.plan-title {
    font-size: 20px;
    font-weight: 600;
    color: var(--primary-color-light);
}

.plan-detail {
    display: grid;
    grid-template-columns: 1fr 120px;
    padding-left: 10px;
}
.plan-detail > div:nth-child(2n){
    text-align: right;
}
</style>