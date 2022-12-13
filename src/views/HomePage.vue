<template>
  <div class="home-page">
    <HeaderVue></HeaderVue>
    <div class="home-page__header">
      <router-link to="/signin" class="home-page__header_button_router">
        <button class="home-page__header_button">Войти</button>
      </router-link>
    </div>
    <div class="main__container">
      <h2 class="main__container_title">Покупайте, торгуйте и храните криптовалоюту на
        <span class="main__container_title_span">MonkeyCoin.</span>
      </h2>

      <div class="main__container_items">
        <div class="main__container_item">
          <p class="main__container_item_text">Регистрируйтесь на платформе MonkeyСoin! Мы предоставляем удобный сервис
            и бонус для новых пользователей: 5% скидку на все валюты, которая позволит вам начать торговать на бирже с
            намного меньшим риском.</p>
          <img class="main__container_item_logo" src="../assets/images/image 1.jpg" alt="Лого">
        </div>

        <h2 class="main__container_title">У нас имеется удобный интерфейс</h2>

        <div class="main__container_item">
          <img class="main__container_item_logo" src="../assets/images/image 2.png" alt="Лого">
          <p class="main__container_item_text">Наш сервис предоставляет удобный интерфейс с сортировкой по нескольким
            параметрам. Кроме того вся необходимая Вам информация уже выведена в компактном табличном виде.</p>
        </div>

        <h2 class="main__container_title">С нами легко заработать. Попробуй уже сейчас.</h2>

        <div class="main__container_item">
          <form class="main__container_form">
            <!-- <input class="main__container_form_input" type="text" placeholder="Введите вашу почту"> -->
            <router-link to="/register"><button
                class="main__container_form_button">Зарегистрироваться</button></router-link>
          </form>
          <img class="main__container_item_logo" src="../assets/images/image 3.jpg" alt="Лого">
        </div>
      </div>
      <footer-vue></footer-vue>
    </div>
  </div>
</template>

<script>

import HeaderVue from '@/components/Header.vue';
import FooterVue from '@/components/Footer.vue';

export default {
  name: 'HomePage',
  components: {
    HeaderVue,
    FooterVue
  }
}
</script>

<style lang="scss">

.home-page {
  position: relative;
}

.home-page__header {
  width: 10rem;
  height: 3rem;
  position: absolute;
  top: 1rem;
  right: 8rem;
  border-radius: 0.75rem;

  &_button {
    height: 3rem;
    width: 10rem;
    margin: auto;
    margin-right: 8rem;
    font-size: 1.25rem;
    color: white;
    border: none;
    border-radius: 0.75rem;
    cursor: pointer;
    font-family: 'Comic Neue', cursive;
  }
}

.home-page__header_button_router {
  background-color: #17191F;
}

.home-page__header:hover {
  opacity: .7;
  transition: .2s;
}

.main__container {
  display: flex;
  flex-direction: column;
  color: white;
  font-family: 'Comic Neue', sans-serif;

  &_title {
    margin: 3rem auto;
    font-size: 3rem;
    width: 75rem;
    text-align: center;

    &_span {
      font-weight: normal;
      font-family: 'Comic Neue', cursive;
    }
  }
}

.main__container_title:first-child {
  margin: 5rem auto 0;
  font-size: 4rem;
}


.main__container_items {
  display: flex;
  flex-direction: column;
  margin-top: 3rem;
}

.main__container_item {
  display: flex;
  gap: 7rem;
  margin: auto 10rem;
  max-height: 34rem;
  max-width: 100rem;

  &_text {
    font-size: 2rem;
  }
}

.main__container_item_logo {
  width: 40rem;
  border-radius: 1.25rem;
}

.main__container_form {
  display: flex;
  flex-direction: column;
  background: none;
  width: 37rem;
  margin: auto;

  &_input {
    margin-bottom: 2rem;
    color: white;
    border-radius: 10px;
    padding: 1rem;
    font-size: 2rem;
    outline: none;
  }
}

.main__container_form_button {
  color: white;
  border-radius: 10px;
  font-size: 2rem;
  padding: 1rem;
  background-color: #F18A2D;
  cursor: pointer;
  border: none;
  width: 37rem;
  font-size: 3rem;
}

.main__container_form_button:hover {
  opacity: .8;
  transition: .2s;
}
</style>
