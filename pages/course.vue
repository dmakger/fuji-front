<template>
  <div id="main-case">
    <HeaderLightBlack />
    <div class="blocks">
    </div>
    <Footer />
  </div>
</template>

<script>
import axios from "axios";
import HeaderLightBlack from "@/components/HeaderLightBlack"
import Footer from "@/components/Footer";

export default {
  name: 'course',
  components: {HeaderLightBlack, Footer},
  data () {
    return {
      courses : []
    }
  },
  async asyncData(ctx) {
    const api = `http://localhost:8000/api/course`
    const { data } = await axios.get(api)
    return {
      courses: data.results,
    }
  }
  // async created () {
  //   const api = `http://localhost:8000/api/course`
  //   const response = await fetch(api)
  //   this.courses = await response.json()
  // }
}
</script>

<style lang="scss" scoped>
//@import "theme/_style/index";
</style>

