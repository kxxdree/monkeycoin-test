<template>
    <div class="main-login">
        <div class="main__header">
            <router-link to="/" class="main__header_logo"><img style="width: 3rem; background-color: #17191F;" src="../assets/images/logo 1.svg"
                    alt="Лого"></router-link>
            <input v-model="searchForCurrency" class="main__header_input" type="text" placeholder="Найти валюту">
            <div class="main-login__balance">
                <input v-if="balanceVisible" type="number" v-model="balance" :placeholder="balance" />
                <p v-else-if="balance == null">Ваш кошелек пуст</p>
                <p v-else>{{ balance }}</p>
                <button @click="openBalance" class="main-login__header_button">Пополнить</button>
            </div>
        </div>
        <div class="main-login__sale-buttons">
            <button @click="openPopup" class="main-login__buy-button login-btn">Купить</button>
            <button @click="openPopup" class="main-login__sale-button login-btn">Продать</button>
        </div>
        <p class="main-login__title">Курс биткоина</p>
        <p></p>
        <p class="main-login__subtitle">{{ prices.disclaimer }}</p>
        <div class="main-login__container">
            <div class="main-login__container_info">
                <p class="main-login__container_info_text">Код валюты</p>
                <!-- <img class="main-login__container_info_text_logo" src="../assets/images/Arrow 2.svg" alt="Arrow"> -->
                <p class="main-login__container_info_text">Наименование валюты</p>
                <!-- <img class="main-login__container_info_text_logo" src="../assets/images/Arrow 2.svg" alt="Arrow"> -->
                <p class="main-login__container_info_text">Цена за 1 Bitcoin</p>
                <!-- <img class="main-login__container_info_text_logo" src="../assets/images/Arrow 2.svg" alt="Arrow"> -->
                <p class="main-login__container_info_text">Символ валюты</p>
                <!-- <img class="main-login__container_info_text_logo" src="../assets/images/Arrow 2.svg" alt="Arrow"> -->
            </div>

            <div v-for="item in prices.bpi" :key="item.id" class="main-login__container_back-data">
                <span>{{ item.code }}</span>
                <span>{{ item.description }}</span>
                <span style="color:green">{{ item.rate }}</span>
                <span>{{ item.symbol }}</span>
            </div>
        </div>
        <popupComponent v-if="isInfoPopupVisible" @openPopup="openPopup" />
    </div>
</template>

<script>
import popupComponent from '../components/popupComponent.vue'
import axios from 'axios'
export default {

    components: {
        popupComponent
    },

    data() {
        return {
            prices: {
                // bpi:{
                //     bpiData:{
                //         code:'',
                //         description:'',
                //         rate:'',
                //         symbol:''
                //     }
                // }
            },
            searchForCurrency: '',
            isInfoPopupVisible: false,
            balance: null,
            balanceVisible: false
        }
    },

    mounted() {

        axios
            .get('https://api.coindesk.com/v1/bpi/currentprice.json')
            .then(response => { (this.prices = response.data); })
            .catch((e) => { (console.log(e.message)); })
    },

    methods: {
        openPopup() {
            this.isInfoPopupVisible ? this.isInfoPopupVisible = false : this.isInfoPopupVisible = true
        },
        openBalance() {
            this.balanceVisible ? this.balanceVisible = false : this.balanceVisible = true
        }
    }
}
</script>

<style lang="scss">
.main-login__balance {
    background-color: #17191F;
}

.main__header {
    height: 5rem;
    background-color: #17191F;
    display: flex;


    &_logo {
        background: none;
        width: 3rem;
        margin-left: 10rem;
    }
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

.main-login__header_button {
    height: 3rem;
    width: 10rem;
    margin: auto;
    margin-right: 8rem;
    font-size: 1.25rem;
    color: #FFB800;
    border: none;
    border-radius: 0.75rem;
    cursor: pointer;
    font-family: 'Comic Neue', cursive;
}

.main-login__header_button:hover {
    opacity: .7;
    transition: .2s;
}


.main-login__sale-buttons {
    display: flex;
    gap: 0.5rem;
    margin-top: 1rem;
}

.login-btn {
    width: 8rem;
    padding: 0.2rem;
    border-radius: 5px;
    border: none;
    background-color: rgb(0, 0, 0, .3);
    cursor: pointer;
    margin: auto;
    font-family: 'Comic Neue', cursive;
    font-size: 1.25rem;


    &:hover {
        opacity: .5;
        transition: .2s;
    }
}

.main-login__buy-button {
    margin-right: 0;
    color: #005600;
}

.main-login__sale-button {
    margin-left: 0;
    color: #8F0000;
}

.main-login__title {
    color: white;
    font-size: 3rem;
    margin-top: 1.5rem;
    margin-left: 11.5rem;
}

.main-login__subtitle {
    color: white;
    font-size: 2rem;
    margin-top: 1.5rem;
    margin-left: 11.5rem;
}

.main-login__container {
    margin-left: 11.5rem;
    margin-top: 3rem;

    &_info {
        background-color: #17191F;
        color: white;
        width: 70rem;
        display: flex;
        justify-content: space-between;
        font-weight: 700;

        &_text {
            background: none;
            margin: auto 0;
            padding: 2px;

            &_logo {
                background: none;
                margin: auto 10rem auto 1rem;
                width: 1rem;
            }
        }
    }
}

.main-login__container_back-data {
    color: white;
    display: flex;
    justify-content: space-between;
    width: 70rem;
    margin-bottom: 3rem;
    margin-top: 2rem;
}
</style>