<template>
    <div class="main__footer">
        <div class="main__footer_container">
            <p class="main__footer_container_text">© MonkeyCode</p>
            <p class="main__footer_container_text">Немного о нас</p>
        </div>
    </div>
</template>
<script>
export default {

}
</script>
<style lang="scss">
.main__footer {
    display: flex;
    margin-top: 3rem;
    height: 3rem;
    background-color: #17191F;


    &_container {
        display: flex;
        justify-content: space-between;
        margin: auto 10rem;
        width: 100%;
        background-color: #17191F;


        &_text {
            color: white;
            opacity: .2;
            font-size: 1rem;
            background: none;
        }
    }
}
</style>