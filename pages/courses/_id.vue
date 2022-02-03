<template>
  <div id="main-case">

    <HeaderImgWhite/>

    <div class="blocks">

      <div class="main">
        <div class="image_dark"></div>
        <div class="main__image-title">
          <img :src="`${info.title_image}`" alt="Title image">
        </div>
        <div class="fixed-container">
          <div class="main__body">
            <div class="main__hello">
              <p class="main__author">{{ course.author.name }}</p>
              <h2 class="main__title">{{ course.title }}</h2>
              <div class="main__link">
                <a href="#">Записаться</a>
              </div>
            </div>
            <div class="main__info">
              <div class="triangle-bottom-right" />
              <div class="main__wrapper">
                <div class="main__content">
                  <div class="main__card">
                    <div class="item-main">
                      <div class="item-main__icon">
                        <img src="~/static/img/star.svg" alt="star">
                      </div>
                      <p class="item-main__title">{{ course.rating }}</p>
                      <p class="item-main__description">из {{ count_comment }} отзывов</p>
                    </div>
                  </div>
                  <div class="main__card">
                    <div class="item-main">
                      <div class="item-main__icon">
                        <img src="~/static/img/people_white.svg" alt="people">
                      </div>
                      <p class="item-main__title">{{ course.members_amount }}</p>
                      <p class="item-main__description">учащихся</p>
                    </div>
                  </div>
                  <div class="main__card">
                    <div class="item-main">
                      <div class="item-main__icon">
                        <img src="~/static/img/clock_white.svg" alt="clock">
                      </div>
                      <p class="item-main__title">{{ hours }} ч</p>
                      <p class="item-main__description">контента</p>
                    </div>
                  </div>
                  <div v-if="course.has_certificate" class="main__card">
                    <div class="item-main">
                      <div class="item-main__icon">
                        <img src="~/static/img/certificate_white.svg" alt="certificate">
                      </div>
                      <p class="item-main__title">Сертификат</p>
                      <p class="item-main__description">для вас</p>
                    </div>
                  </div>
                </div>
              </div>
              <div class="triangle-bottom-left" />
            </div>
          </div>
        </div>
      </div>

      <div class="gradient">

        <div class="goal">
          <div class="fixed-container">
            <div class="goal__body block__body">
              <div class="goal__title__wrapper title__wrapper">
                <h3 class="goal__title title title_border-bottom">Цель курса</h3>
              </div>
              <div class="goal__content block__content">
                <p class="goal__description block__description">{{ info.goal_description }}</p>
              </div>
            </div>
          </div>
        </div>

        <div class="fit">
          <div class="fixed-container">
            <div class="fit__body block__body">
              <div class="fit__title__wrapper title__wrapper">
                <h3 class="fit__title title title_border-bottom">Кому подойдёт этот курс</h3>
              </div>
              <div class="fit__content block__content">
                <div v-for="fit in info.fit" :key="fit.title"
                  class="item-fit">
                  <h5 class="item-fit__subtitle">{{ fit.title }}</h5>
                  <p class="item-fit__description block__description">{{ fit.description }}</p>
                </div>
              </div>
            </div>
          </div>
        </div>

        <div class="skill">
          <div class="fixed-container">
            <div class="skill__body block__body">
              <div class="skill__title__wrapper title__wrapper">
                <h3 class="skill__title title title_border-bottom">Кому подойдёт этот курс</h3>
              </div>
              <div class="skill__content block__content">
                <div v-for="(skill, itemObjKey) in info.skill" :key="skill.name"
                     class="skill__card">
                  <div class="item-skill">
                    <div class="item-skill__count">
                      <h5>{{ itemObjKey + 1 }}</h5>
                    </div>
                    <p class="item-skill__description block__description">{{ skill.name }}</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <div v-if="course.has_certificate" class="certificate">
          <div class="fixed-container">
            <div class="certificate__body block__body">
              <div class="certificate__text block__content">
                <div class="certificate__title__wrapper title__wrapper">
                  <h3 class="certificate__title title title_border-bottom">Сертификат</h3>
                </div>
                <p class="certificate__description block__description">Вы получаете сертификат о повышении квалификации
                  Он подтвердит, что вы проходили данный курс</p>
                <div class="certificate__author__wrapper">
                  <img :src="`${course.author.avatar_url}`" alt="Avatar author">
                  <p class="certificate__author">{{ course.author.name }}</p>
                </div>
              </div>
              <div class="certificate__title-image">
                <img src="~/static/img/certificate_title.png" alt="certificate title">
              </div>
            </div>
          </div>
        </div>

      </div>

      <div class="info">
        <div class="fixed-container">
          <div class="info__body">
            <div class="info-title__wrapper">
              <h3 class="info-title title_center">Программа курса</h3>
            </div>
            <div class="info-general">
              <div class="info-general__card">
                <div class="item-info-general">
                  <div class="item-info-general__title-block">
                    <h5 class="item-info-general__title">{{ general_amount.modules_amount }}</h5>
                  </div>
                  <p class="item-info-general__description">Темы</p>
                </div>
              </div>
              <div class="info-general__card">
                <div class="item-info-general">
                  <div class="item-info-general__title-block">
                    <h5 class="item-info-general__title">{{ general_amount.lessons_amount }}</h5>
                  </div>
                  <p class="item-info-general__description">Уроков</p>
                </div>
              </div>
              <div class="info-general__card">
                <div class="item-info-general">
                  <div class="item-info-general__title-block">
                    <h5 class="item-info-general__title">{{ general_amount.steps_amount }}</h5>
                  </div>
                  <p class="item-info-general__description">Степов</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

<!--      <div class="info-cards">-->
<!--        <div class="fixed-container">-->
<!--          <div class="info-cards__body">-->
<!--            <div v-for="module in modules" :key="module.title"-->
<!--              class="info-cards__card">-->
<!--              <div class="item-info-cards">-->
<!--                <div class="item-info__summary item-info__summary">-->
<!--                  <div class="item-info__summary-title-block">-->
<!--                    <p class="item-info__summary-title">{{ module.lessons_amount }} уроков</p>-->
<!--                  </div>-->
<!--                </div>-->
<!--              </div>-->
<!--            </div>-->
<!--          </div>-->
<!--        </div>-->
<!--      </div>-->

    </div>

    <Footer/>

  </div>
</template>

<script>
import axios from "axios";
import HeaderLightBlack from "@/components/HeaderLightBlack"
import Footer from "@/components/Footer";

export default {
  // name: 'course_detail',
  components: {HeaderLightBlack, Footer},
  async asyncData({params}) {
    const host = `http://localhost:8000`
    const api = `${host}/api/courses/${params.id}/`
    const data = (await axios.get(api)).data

    data.info.title_image = host + data.info.title_image
    data.course.author.avatar_url = host + data.course.author.avatar_url
    const hours = Math.floor(data.course.duration_in_minutes / 60)
    const modules = data.module

    return {
      course: data.course,
      info: data.info,
      count_comment: data.info.comments.length,
      hours: hours,
      modules: modules,
      general_amount: getGeneralAmount(modules),
    }

    function getGeneralAmount(modules) {
      let modules_amount = modules.length
      let lessons_amount = 0
      let steps_amount = 0
      for (const i in modules) {
        lessons_amount += modules[i]['lessons_amount']
        for (const j in modules[i]['lesson']) {
          steps_amount += modules[i]['lesson'][j]['steps_amount']
        }
      }

      return {
        modules_amount: modules_amount,
        lessons_amount: lessons_amount,
        steps_amount: steps_amount
      }
    }

  },
}
</script>

<style lang="scss" scoped>
  @import "theme/_style/_course_detail";
</style>
