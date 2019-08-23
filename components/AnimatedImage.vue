<template>
  <div>
    <div id="roly" class="image">
      <div
        class="image-roly"
      >
        <img class="mobile-show image-roly__mobile" src="../assets/images/img-roly-poly-static@2x.png" alt="">
        <img class="mobile-hide" src="../assets/images/img-roly-poly.svg" alt="">
      </div>
      <div class="image-roly-bg mobile-hide" />
      <div
        class="image-light image-light-1 mobile-hide"
      />
      <div
        class="image-light image-light-2 mobile-hide"
      />
      <div
        class="image-light image-light-3 mobile-hide"
      />
      <div
        class="image-light image-light-4 mobile-hide"
      />

      <div
        v-for="(el, i) in 4"
        :key="i"
        class="image-light mobile-hide"
        :class="{
          animated: isHovered,
          heartBeat: isHovered,
          [`image-light-${i}`]: true
        }"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: 'AnimatedImage',
  data: () => ({
    isHovered: false
  })
}
</script>

<style lang="scss" scoped>
@import "../assets/styles/animate";

.image {
  position: relative;

  &:hover {
    .image-roly {
      -webkit-animation-duration: 1s;
      animation-duration: 1s;
      -webkit-animation-fill-mode: both;
      animation-fill-mode: both;
      -webkit-animation-name: wobble;
      animation-name: wobble;
    }

  .image-light {
    -webkit-animation-duration: 1s;
    animation-duration: 1s;
    -webkit-animation-fill-mode: both;
    animation-fill-mode: both;
    -webkit-animation-name: heartBeat;
    animation-name: heartBeat;
  }
  }
}

.image .image-roly {
  max-width: 247px;
  position: relative;
  z-index: 5;
  margin: 0 auto;
}

.image-roly__mobile{
  margin: 0 auto;
}

.image .image-roly img {
  height: 100%;
  width: auto;
}

.image .image-roly-bg {
  width: 305px;
  height: 75px;
  background: url(../assets/images/img-bg.svg) no-repeat;
  background-size: 100%;
  position: absolute;
  z-index: 1;
  bottom: -31px;
  left: 3px;
}

.image .image-light {
  position: absolute;
  top: 0;
}

.image .image-light-1 {
  width: 90px;
  height: 46px;
  top: 123px;
  left: -53px;
  background: url(../assets/images/img-light-1.svg) no-repeat;
  background-size: 100%;
}

.image .image-light-2 {
  width: 75px;
  height: 69px;
  top: 66px;
  left: -16px;
  background: url(../assets/images/img-light-2.svg) no-repeat;
  background-size: 100%;
}

.image .image-light-3 {
  width: 75px;
  height: 69px;
  right: -28px;
  top: 67px;
  background: url(../assets/images/img-light-3.svg) no-repeat;
  background-size: 100%;
}

.image .image-light-4 {
  width: 91px;
  height: 46px;
  right: -66px;
  top: 123px;
  background: url(../assets/images/img-light-4.svg) no-repeat;
  background-size: 100%;
}
</style>
