<template>
    <view class="header">
        <text class="title">{{ title }}</text>
    </view>
</template>

<script>
export default {
props: [
    'title'
] 
}
</script>

<style>
.header {
    background-color: #000000;
    height: 60;
    justify-content: center;
    align-items: center;
}
.title {
    color: #ffffff;
    font-size: 28;
    font-weight: 900;
    text-transform: uppercase;
}
</style>