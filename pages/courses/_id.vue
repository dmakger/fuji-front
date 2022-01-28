<template>
  <div id="main-case">

    <HeaderImgWhite/>

    <div class="blocks">
      <div class="main" :style="{ backgroundImage: `url(${info.title_image})` }">
        <div class="fixed-container">
          <div class="main__body">
            <div class="main__hello">
              <p class="main__author">{{ course.author }}</p>
              <h2 class="main__title">{{ course.title }}</h2>
              <div class="main_link">
                <a href="#">Перейти</a>
              </div>
            </div>
            <div class="main__info">
              <div class="main__info main__wrapper">
                <div class="main__info main__content">
                  <div class="main__card">
                    <div class="item-main">
                      <div class="item-main__icon">
                        <img src="img/star.svg" alt="star">
                      </div>
                      <p class="item-main__title">{{ course.rating }}</p>
                      <p class="item-main__description">из {{ count_comment }} отзывов</p>
                    </div>
                    <div class="item-main">
                      <div class="item-main__icon">
                        <img src="img/people.svg" alt="people">
                      </div>
                      <p class="item-main__title">{{ course.members_amount }}</p>
                      <p class="item-main__description">учащихся</p>
                    </div>
                    <div class="item-main">
                      <div class="item-main__icon">
                        <img src="img/clock.svg" alt="clock">
                      </div>
                      <p class="item-main__title">{{ hours }} ч</p>
                      <p class="item-main__description">контента</p>
                    </div>
                    <div v-if="course.has_certificate" class="item-main">
                      <div class="item-main__icon">
                        <img src="img/star.svg" alt="star">
                      </div>
                      <p class="item-main__title">Сертификат</p>
                      <p class="item-main__description">FUJI, {{ course.author }}}</p>
                    </div>
                  </div>
                </div>
              </div>
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
    return {
      course: data.course,
      info: data.info,
      count_comment: data.info.comments.length,
      hours: data.course.duration_in_minutes/60,
    }
  },
}
</script>

<style lang="scss" scoped>
  @import "theme/_style/_course_detail";
</style>
