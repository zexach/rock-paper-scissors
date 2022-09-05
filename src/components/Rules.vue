<template>
    <div class="rules-container">
        <h1>RULES</h1>
        <img src="../img/image-rules.svg">
    </div>
</template>

<style scoped>
    .rules-container{
        width: 500px;
        height: 520px;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        border-radius: 5px;
        background-color: rgb(235, 235, 235);
        box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
        color: rgb(153, 153, 153);
        font-size: 15px;
        position: absolute;
        z-index: 1;
        }
    h1{
        font-size: 40px;
        font-weight: 600;
        margin-bottom: 50px;
    }
    img{
        width: 300px;
    }
    @media screen and (max-width: 500px) {
        .rules-container{
            width: 340px;
            height: 520px;
        }
    }
</style>