<template>
    <div class="auth__page">
        <header-vue></header-vue>
        <div class="home-page__header">
            <router-link to="/signin" class="home-page__header_button_router">
                <button class="home-page__header_button">Войти</button>
            </router-link>
        </div>
        <div class="auth__container-page">
            <h1 class="auth-page__title">Регистрация</h1>
            <!-- <p class="auth-page__subtitle">
                <router-link to="/signin" class="auth-page__subtitle_link">Есть аккаунт?</router-link>
            </p> -->
            <form action="#" class="auth__form">
                <input v-model="userName" type="text" class="auth__input" placeholder="Имя пользователя" required>
                <input v-model="userEmail" type="email" class="auth__input" placeholder="Email" required>
                <input v-model="userPassword" type="password" class="auth__input" placeholder="Пароль" required>
                <button @click.prevent="sendForm" class="auth__sign-button">Зарегистрироваться</button>
            </form>
        </div>
        <footer-vue></footer-vue>
    </div>
</template>

<script>
import HeaderVue from '@/components/Header.vue';
import FooterVue from '@/components/Footer.vue';

import axios from 'axios'

export default {
    components: {
        HeaderVue,
        FooterVue
    },

    data() {
        return {
            userName: '',
            userEmail: '',
            userPassword: '',
            info: []
        }
    },
    methods: {
        sendForm() {
            let formData = new FormData();
            formData.append('title', this.userName)
            formData.append('body', this.userEmail)
            formData.append('userId', this.userPassword)
            axios
                .post('https://jsonplaceholder.typicode.com/posts', formData)
                .then(response => { (this.info = response.data) }, this.$router.push({ path: '/mainlogin' }))
                .catch((e) => { (console.log(e.message)); })
        }
    }
}
</script>

<style lang="scss">
.auth__page {
    background-color: #0D1017;
}

.auth__container-page {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 60%;
    margin: auto;
}

.auth-page__title {
    font-size: 4rem;
    font-weight: normal;
    color: white;
    margin-top: 2rem;
}

.auth-page__subtitle {
    font-size: 2rem;
    margin: 1rem 0 3rem;
    text-decoration: none;
    height: 3rem;

    &_link {
        text-decoration: none;
        color: white;
        opacity: .5;
    }
}

.auth-page__subtitle:hover {
    opacity: .5;
    transition: .2s;
}

.auth__form {
    display: flex;
    flex-direction: column;
    gap: 2rem;
    margin-bottom: 3rem;
    margin-top: 2rem;
}

.auth__input {
    width: 32rem;
    font-size: 2rem;
    text-align: center;
    padding: 1rem;
    text-align: left;
    border-radius: 0.5rem;
    outline: none;
    background-color: white;

}

.auth__input:hover {
    opacity: .9;
    transition: .2s;
}

.auth__sign-button {
    background: none;
    border: none;
    background-color: #F18A2D;
    border-radius: 0.75rem;
    color: white;
    align-self: flex-end;
    font-size: 1.5rem;
    padding: 2rem;
    cursor: pointer;

}

.auth__sign-button:hover {
    opacity: .8;
    transition: .2s;
}
</style>