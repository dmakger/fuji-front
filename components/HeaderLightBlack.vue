<template>
  <header>
    <div class="fixed-container">
      <div class="header__body">
        <div class="case-logo">
          <nuxt-link to="/" class="logo">FUJI</nuxt-link>
        </div>

        <nav class="nav">
          <div class="nav__menu">
            <nuxt-link to="/course" class="item-nav__menu">Курсы</nuxt-link>
            <nuxt-link to="/" class="item-nav__menu">Лекции</nuxt-link>
            <nuxt-link to="/" class="item-nav__menu">Организации</nuxt-link>
          </div>

          <div id="nav__sign">
            <nuxt-link to="/signin">Вход</nuxt-link>
          </div>
        </nav>
      </div>
    </div>
  </header>
</template>

<script>
export default{
  name: "HeaderLightBlack",
}
</script>

<style lang="scss">
@import "../theme/_style/header";
@include header-light($fc-white, $fc-black, $bgc-purple);
</style>
