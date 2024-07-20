<template>
    <div class="sticky-header">
        <div class="avatar"></div>
        <div class="tools">
            <div class="circle">
                <img src="../assets/hamburger.png" alt="hamburger" width="32" height="32">
            </div>
            <div class="circle msg">
                <img src="../assets/notification.png" alt="notification" width="32" height="32">
            </div>
        </div>
    </div>
</template>
<style>
.avatar{
    margin-bottom: 1rem;
    width: 4rem;
    height: 4rem;
    background: url(../assets/avatar.png);
    background-size: 180%;
    background-position: 50%;
    background-repeat: no-repeat;
    border-radius: 50%;
}
.tools{
    position: fixed;
    top: 1rem;
    right: 10px;
}
.msg{
    position: relative;
}
.msg::after{
    content: '3';
    position: absolute;
    width: 1.5rem;
    height: 1.5rem;
    text-align: center;
    border-radius: 50%;
    bottom: -8px;
    right: 0;
    color: #fff;
    font-weight: 500;
    background-color: var(--primary-color);
}
</style>