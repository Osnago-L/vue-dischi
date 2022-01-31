<template>
    <div class="header">
        <img src="../assets/img/green_logo.png" alt="">
    </div>
</template>

<script>
export default {
    name: "Header"
}
</script>

<style lang="scss" scoped>
@import "../assets/style/partial/variables.scss";
    .header{
        width: 100%;
        height: $header-height;
        background-color: #2e3a46;
        padding: 0 20px;
        display: flex;
        align-items: center;
       
        img{
            width: 40px;
        }
    }
</style>