<template>
    <div class="main__header">
        <router-link to="/" class="main__header_logo">
            <img class="main__header_logo-item" src="../assets/images/logo 1.svg" alt="Лого">
        </router-link>
        <input class="main__header_input" type="text" placeholder="Найти валюту">
    </div>
</template>
<script>

export default {

}
</script>

<style lang="scss">

.main__header {
    height: 5rem;
    background-color: #17191F;
    display: flex;
    width: 100%;

    &_logo {
        background: none;
        width: 3rem;
        margin-left: 10rem;

        &-item {
            background: none;
            margin-top: 1rem;
        }
    }
}

.main__header_input {
    height: 3rem;
    width: 18rem;
    margin: auto auto auto 2rem;
    color: rgb(255, 255, 255, .4);
    padding: 1rem;
    outline: none;
    border: none;
    border-radius: 5px;
}
</style>