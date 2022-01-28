<template>
  <div id="main-case">

    <HeaderLightBlack/>

    <div class="blocks">
      <h1>Bruh</h1>
    </div>

    <Footer/>

  </div>
</template>

<script>
import axios from "axios";
import HeaderLightBlack from "@/components/HeaderLightBlack"
import Footer from "@/components/Footer";

export default {
  // name: 'slug',
  components: {HeaderLightBlack, Footer},
  async asyncData({params}) {
    const api = `http://localhost:8000/api/courses/${params.id}/`
    const data = await axios.get(api)
    return {
      course: data.data,
    }
  },

  // async asyncData({params}) {
  //   const post = await axios.get(`http://localhost:8000/api/course/${params.slug}`);
  //   return {
  //     post: post.data,
  //   }
  // },
}
</script>

<style scoped>

</style>
