<template>
  <div id="main-case">

    <HeaderPurpleWhite />

    <div class="blocks">

      <div class="base">
        <div class="fixed-container">
          <div class="base__body">
            <div class="base__info">
              <h2 class="base__title">Стань умнее вместе с FUJI</h2>
              <p class="base__description">Правильно произносить «Фудзи»</p>
            </div>
            <div class="base__icon">
              <img src="img/mountain.gif" alt="Горы">
            </div>
          </div>
        </div>
      </div>

      <div class="section">
        <div class="fixed-container">
          <div class="section__body">
            <div class="section__header">
              <h3 class="section__title">Наши разделы</h3>
              <div class="line"/>
            </div>
            <div class="section__content">
              <div class="section__card">
                <div class="item-section">
                  <div class="item-section__text">
                    <h5 class="item-section__title">Курсы</h5>
                    <p class="item-section__description">Серия из лекций позволяющая изучить какой-либо предмет или обучиться навыку</p>
                    <div class="item-section__link">
                      <nuxt-link to="/course">Перейти</nuxt-link>
                    </div>
                  </div>
                  <div class="item-section__icon">
                    <img src="img/book.svg" alt="Карандаш">
                  </div>
                </div>
              </div>
              <div class="section__card">
                <div class="item-section">
                  <div class="item-section__text">
                    <h5 class="item-section__title">Организации</h5>
                    <p class="item-section__description">Это люди, компании, школы, которые создают для вас весь контент (курсы, лекции)</p>
                    <div class="item-section__link">
                      <nuxt-link to="#">Перейти</nuxt-link>
                    </div>
                  </div>
                  <div class="item-section__icon">
                    <img src="img/pencil.svg" alt="Карандаш">
                  </div>
                </div>
              </div>
              <div class="section__card">
                <div class="item-section">
                  <div class="item-section__text">
                    <h5 class="item-section__title">Лекции</h5>
                    <p class="item-section__description">Структурированный разбор темы</p>
                    <div class="item-section__link">
                      <nuxt-link to="#">Перейти</nuxt-link>
                    </div>
                  </div>
                  <div class="item-section__icon">
                    <img src="img/sheet.svg" alt="Карандаш">
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="mobile">
        <div class="fixed-container">
          <div class="mobile__body">
            <div class="mobile__text">
              <h4 class="mobile__title">Изучайте курсы везде</h4>
              <p class="mobile__description">FUJI доступен и на Android</p>
              <div class="mobile__google-play">
                <img src="img/google_play.svg" alt="Доступно в Google Play">
              </div>
            </div>
            <div class="mobile__icon">
              <img src="img/android.svg" alt="android">
            </div>
          </div>
        </div>
      </div>
    </div>

    <Footer />

  </div>
</template>

<script>
import HeaderPurpleWhite from "@/components/HeaderPurpleWhite"
import Footer from "@/components/Footer";

export default {
  name: 'IndexPage',
  components: {HeaderPurpleWhite, Footer}
}
</script>

<style lang="scss" scoped>
  @import "theme/_style/index";
</style>
