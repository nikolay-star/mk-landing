<template>
  <div class="wrapper">
    <div ref="circle" class="circle">
      <img
        src="/images/bg-white.svg"
        class="circle__img"
        alt="background"
      >
    </div>
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
          <img
            src="/images/img-logo.svg"
            alt="Бизнес неваляжка"
          >
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
          href="#"
          class="link"
        >
          {{ btnText }}
        </a>
      </div>
    </div>
    <a
      href="#"
      class="link-mobile"
    >
      {{ btnText }}
    </a>
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
  },
  head () {
    return {
      title: 'Бизнес неваляжка',
      meta: [
        { hid: 'description', name: 'description', content: 'Мастер класс Оли Оли Рыжик' }
      ]
    }
  }
}
</script>

<style lang="scss">
  @import '../assets/styles/variables.scss';
  @import "../static/fonts/GothamPro/stylesheet.css";
  @import "../assets/styles/main.scss";

  .wrapper{
    position: relative;
    padding-bottom: 80px;
    min-height: 100vh;
  }

  .container{
    position: relative;
    max-width: 260px;
    margin: 0 auto;

    @media (min-width: $sm) {
      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: flex-end;
      height: 100vh;
      min-height: 700px;
      min-width: 100%;
    }

    @media (min-width: $md) {
      justify-content: center;
    }
  }

  .circle{
    height: 98%;
    margin-top: 2%;
    position: absolute;
    display: flex;
    justify-content: center;
    top: 0;
    left: 0;
    right: 0;
    width: 100%;
    z-index: 0;
    overflow: hidden;

    @media (min-width: $sm) {
      height: 92%;
      margin-top: 4%;
      margin-bottom: 4%;
    }

    @media (min-width: $md) {
      height: 120%;
      margin-top: -10%;
    }

    &__img{
      display: flex;
      flex-direction: column;
      justify-content: center;
      min-height: 100%;
    }
  }

  .main-img {
    width: 100%;
    max-width: 280px;
    margin-bottom: 40px;

    @media (min-width: $sm) {
      max-width: 357px;
    }

    img{
      display: block;
      width: 100%;
    }
  }

  .link-mobile{
    display: block;
    text-decoration: none;
    width: 100%;
    height: 60px;
    line-height: 60px;
    text-align: center;
    background-color: $primary;
    position: fixed;
    z-index: 10;
    bottom: 0;
    left: 0;

    font-size: 18px;
    font-weight: bold;
    letter-spacing: 1px;
    color: $dark;
    text-transform: uppercase;

    @media (min-width: $sm) {
      display: none;
    }
  }

  .link{
    display: none;
    width: 192px;
    height: 56px;
    border: solid 3px $dark;
    text-align: center;
    line-height: 52px;
    text-decoration: none;
    text-transform: uppercase;
    color: $dark;
    background: rgba(0, 0, 0, 0);
    margin-left: $tempPadding;
    font-weight: bold;

    &:hover{
      background: rgba(0, 0, 0, 0.1);
    }

    @media (min-width: $sm) {
      display: inline-block;
      margin-left: $tempPaddingMd;
    }
  }

  .img{
    padding-top: 60px;
    margin: 0 auto 40px;

    @media (min-width: $sm) {
      padding-top: 0;
      margin: 0 105px 0 0;
    }

    @media (min-width: $md) {
      margin: 0 155px 0 0;
    }

    @media (min-width: $lg) {
      margin: 0 235px 0 0;
    }
  }

  .date{
    margin-bottom: 40px;
    padding-left: $tempPadding;
    font-weight: bold;
    letter-spacing: 1px;
    color: $dark;
    text-transform: uppercase;

    @media (min-width: $sm) {
      padding-left: $tempPaddingMd;
    }
  }

  .title{
    padding-left: $tempPadding;
    margin-bottom: 40px;
    text-transform: uppercase;
    line-height: 1;

    @media (min-width: $sm) {
      padding-left: $tempPaddingMd;
    }

    &__descr{
      display: block;
      font-size: 18px;
      letter-spacing: 1px;
      color: $dark;
      margin-bottom: 14px;
      font-weight: normal;
    }

    &__name{
      display: block;
      font-size: 30px;
      font-weight: bold;
      letter-spacing: 1px;
      color: $dark;
    }
  }

  .subtitle{
    margin-bottom: 20px;
    text-transform: uppercase;
    padding-left: $tempPadding;
    color: $dark;
    line-height: 1.44;
    letter-spacing: 1px;
    max-width: 280px;
    font-weight: normal;
    font-size: 18px;

    @media (min-width: $sm) {
      padding-left: $tempPaddingMd;
    }
  }

  .experts{
    margin-bottom: 20px;
    padding-left: $tempPadding;

    @media (min-width: $sm) {
      padding-left: $tempPaddingMd;
    }

    &__item{
      font-size: 18px;
      font-weight: bold;
      line-height: 1.44;
      letter-spacing: 1px;
      color: $dark;
    }
  }
</style>
