<template>
    <div class="gift">
        <div class="gift-cover"></div>
        <div class="gift-body"></div>
        <div class="gift-ribbon-vertical"></div>
        <div class="gift-ribbon-horizontal"></div>
    </div>
</template>

<script>
    export default {
        name: "Gift"
    }
</script>

<style>
    .gift {
        position: relative;
        display: flex;
        flex-direction: column;
        align-items: center;
        z-index: 10;
    }

    .gift-cover {
        background-color: #1E90FF;
        height: 25px;
        width: 110px;
    }

    .gift-body {
        background-color: #4169E1;
        height: 60px;
        width: 90px;
    }

    .gift-ribbon-vertical {
        position: absolute;
        height: 85px;
        width: 15px;
        background-color: #E00;
    }

    .gift-ribbon-horizontal {
        position: absolute;
        top: 40px;
        height: 15px;
        width: 90px;
        background-color: #E00;
    }
</style>