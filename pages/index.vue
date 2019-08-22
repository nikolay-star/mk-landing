<template>
  <div class="container">
    <div class="img">
      <AnimatedImage />
    </div>
    <div class="description">
      <div class="date">
        {{ date }}
      </div>
      <h1 class="title">
        <span class="title__descr">
          {{ title.text }}
        </span>
        <span class="title__name">
          {{ title.name }}
        </span>
      </h1>
      <div class="main-img">
        <img src="" alt="">
      </div>
      <h2 class="subtitle">
        {{ subtitle }}
      </h2>
      <ul class="experts">
        <li
          v-for="(expert, index) in experts"
          :key="index"
          class="experts__item"
        >
          {{ expert }}
        </li>
      </ul>
      <a
        href="http://roly-poly.com.ua"
        class="link"
      >
        {{ btnText }}
      </a>
    </div>
  </div>
</template>

<script>
import AnimatedImage from '~/components/AnimatedImage'

export default {
  components: {
    AnimatedImage
  },
  async asyncData ({ $axios }) {
    const data = await $axios.$get('/data.json')

    return {
      ...data
    }
  }
}
</script>

<style lang="scss">
  @import '../assets/variables.scss';

</style>
