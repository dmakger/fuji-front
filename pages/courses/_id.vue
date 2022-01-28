<template>
  <div id="main-case">

    <HeaderImgWhite/>

    <div class="blocks">

      <div class="main">
        <div class="image_dark"></div>
        <div class="main__image-title">
          <img :src="`${info.title_image}`" alt="">
        </div>
        <div class="fixed-container">
          <div class="main__body">
            <div class="main__hello">
              <p class="main__author">{{ course.author }}</p>
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
            <div class="goal__body">
              <div class="goal__title__wrapper">
                <h3 class="goal__title">Цель курса</h3>
              </div>
              <p class="goal__description">{{ info.goal_description }}</p>
            </div>
          </div>
        </div>
        <div class="fit">
          <div class="fixed-container">
            <div class="fit__body">

            </div>
          </div>
        </div>
      </div>

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
    const api = `http://localhost:8000/api/courses/${params.id}/`
    const data = (await axios.get(api)).data
    data.info.title_image = "http://localhost:8000" + data.info.title_image

    const hours = Math.floor(data.course.duration_in_minutes / 60)

    return {
      course: data.course,
      info: data.info,
      count_comment: data.info.comments.length,
      hours: hours,
    }
  },
}
</script>

<style lang="scss" scoped>
  @import "theme/_style/_course_detail";
</style>
