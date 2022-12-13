<template>
    <div class="main__header">
        <img class="main__header_logo" src="../assets/images/logo 1.svg" alt="Лого">
        <input class="main__header_input" type="text" placeholder="Найти валюту">
    </div>
</template>
<script>

export default {

}
</script>

<style>

.main__header {
    height: 5rem;
    background-color: #17191F;
    display: flex;
    width: 100%;
}

.main__header_logo {
    background: none;
    width: 3rem;
    margin-left: 10rem;
}

.main__header_input {
    height: 3rem;
    width: 18rem;
    margin: auto auto auto 3rem;
    color: rgb(255, 255, 255, .4);
    padding: 1rem;
    outline: none;
    border: none;
    border-radius: 5px;
}
</style>