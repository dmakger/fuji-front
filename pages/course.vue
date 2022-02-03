<template>
  <div id="main-case">

    <HeaderLightBlack/>

    <div class="blocks">

      <div class="title">
        <div class="fixed-container">
          <div class="title__body">
            <h1>Курсы</h1>
          </div>
        </div>
      </div>

      <div class="search">
        <div class="fixed-container">
          <div class="search__body">
            <div class="myself-search">
              <form action="" method="get">
                <input name="q" type="search" placeholder="Поиск...">
                <div class="myself-search__send">
                  <input type="submit" value="">
                </div>
              </form>
            </div>
          </div>
        </div>
      </div>

      <div class="sorting">
        <div class="fixed-container">
          <div class="sorting__body">
            <span class="item-sorting">
              <p class="item-sorting__title">По популярности</p>
              <img src="img/big_small.svg" alt="" class="item-sorting__icon">
            </span>
            <span class="item-sorting">
                <p class="item-sorting__title">По рейтингу</p>
                <img src="img/big_small.svg" alt="" class="item-sorting__icon">
            </span>
            <span class="item-sorting">
                <p class="item-sorting__title">По цене</p>
                <img src="img/big_small.svg" alt="" class="item-sorting__icon">
            </span>
            <span class="item-sorting">
                <p class="item-sorting__title">По названию</p>
                <img src="img/big_small.svg" alt="" class="item-sorting__icon">
            </span>
            <span class="item-sorting">
                <p class="item-sorting__title">По дате добавления</p>
                <img src="img/big_small.svg" alt="" class="item-sorting__icon">
            </span>
          </div>
        </div>
      </div>

      <div class="course-raw">
        <div class="fixed-container">
          <div class="course-raw__body">
            <div class="course-raw__course course">
              <nuxt-link v-for="course in courses" :to="`/courses/${course.id}`" :key="course.id" class="item-course">
                <div class="item-course__wrapper">
                  <div class="item-course__main-info">
                    <div class="item-course__icon">
                      <img :src="course.image" alt="Изображение курса course.title">
                    </div>
                    <div class="item-course__text">
                      <p class="item-course__title">{{ course.title }}</p>
                      <p class="item-course__author">{{ course.author.name }}</p>
                      <p class="item-course__description">{{ course.description }}</p>
                    </div>
                  </div>
                  <div class="item-course__info">
                    <div class="info-item-course">
                      <span class="info-item-course__tag">
                        <img src="img/star.svg" alt="Количество отзывов">
                        <p>{{ course.rating }}</p>
                      </span>
                      <span class="info-item-course__tag">
                        <img src="img/people.svg" alt="Количество людей записавшиеся на курс">
                        <p>{{ course.members_amount }}</p>
                      </span>
                      <span class="info-item-course__tag">
                        <img src="img/clock.svg" alt="Количество часов на прохождение">
                        <p>{{ course.duration_in_minutes }}</p>
                      </span>
                      <span v-if="courses.has_certificate" class="info-item-course__tag">
                        <img src="img/certificate.svg" alt="Сертификат">
                        <p>сертификат</p>
                      </span>
                    </div>
                    <span v-if="course.price === 0" class="item-course__price">
                      <p class="green">Бесплатно</p>
                    </span>
                    <span v-else class="item-course__price">
                      <p class="purple">{{ course.price }}</p>
                      <img src="/img/rub.svg" alt="Символ рубля">
                    </span>
                  </div>
                </div>
              </nuxt-link>
            </div>
            <div class="course-raw__filter">
              <div class="filter">
                <div class="item-filter">
                  <h6>Цена</h6>
                  <div class="item-filter__content radio">
                    <input type="radio" id="price__all" name="price" value="1" checked>
                    <label for="price__all">Любая</label>
                    <input type="radio" id="price__free" name="price" value="2">
                    <label for="price__free">Бесплатно</label>
                    <input type="radio" id="price__payable" name="price" value="3">
                    <label for="price__payable">Платно</label>
                  </div>
                </div>
                <div class="item-filter" id="status">
                  <h6>Статус</h6>
                  <div class="item-filter__content checkbox">
                    <input type="checkbox" id="checkbox__all" name="status" value="1">
                    <label for="checkbox__all">Не добавленное</label>
                    <input type="checkbox" id="checkbox__free" name="status" value="2">
                    <label for="checkbox__free">Добавленное</label>
                    <input type="checkbox" id="checkbox__payable" name="status" value="3">
                    <label for="checkbox__payable">Пройденное</label>
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
  name: 'test',
  components: {HeaderLightBlack, Footer},
  async asyncData(ctx) {
    const api = `http://localhost:8000/api/courses`
    const {data} = await axios.get(api)
    return {
      courses: data.results,
    }
  }
}
</script>

<style lang="scss" scoped>
@import "theme/_style/course";
</style>

