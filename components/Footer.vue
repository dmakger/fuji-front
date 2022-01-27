<template>
  <footer>
    <div class="fixed-container">
      <div class="footer__body">
        <div class="footer__case-logo">
          <div class="footer__logo">
            <nuxt-link to="/" class="purple logo">FUJI</nuxt-link>
          </div>
        </div>

        <div class="footer__menu">
          <p class="footer__title">Меню</p>
          <div class="footer__link">
            <nuxt-link to="/course">Курсы</nuxt-link>
            <nuxt-link to="#">Лекции</nuxt-link>
            <nuxt-link to="#">Организации</nuxt-link>
          </div>
        </div>

        <div class="footer__about">
          <p class="footer__title">О нас</p>
          <div class="footer__link">
            <nuxt-link to="/">Контакты</nuxt-link>
            <nuxt-link to="/">Вакансии</nuxt-link>
          </div>
        </div>

        <div class="footer__media">
          <nuxt-link to="#" class="footer__media-link">
            <img src="img/instagram.png" alt="Мы в инсте">
          </nuxt-link>
          <nuxt-link to="#" class="footer__media-link">
            <img src="img/vk.png" alt="Группа в вк">
          </nuxt-link>
          <nuxt-link to="#" class="footer__media-link">
            <img src="img/telegram.svg" alt="Группа в вк">
          </nuxt-link>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
  export default {
    name: "Footer",
  }
</script>

<style lang="scss">
  @import "../theme/_style/footer";
</style>
