<template>
  <q-page class="flex flex-center">
    <lottie
      :options="defaultOptions"
      :height="220"
      :width="180"
      v-on:animCreated="handleAnimation"
    />
  </q-page>
</template>

<script>
import Lottie from 'vue-lottie';
import * as animationData from 'assets/json/splash.json';

export default {
  name: 'PageIndex',
  components: { Lottie },
  data() {
    return {
      defaultOptions: {
        animationData: animationData.default, // 실제 애니메이션 json 데이터 경로로 작성하기도 함 (animationData.default 라고 해줘야 한다네?)
        autoplay: true, // 자동 재생 (생략 시 true)
        loop: true, // 반복 재생 (생략 시 true)
        // container: , // 애니메이션을 어디에 삽입할 것인지 (자바스크립트에선 querySelector로 선택자로 작성하던데 vue에선 생략해도 되나봄?)
        // renderer: 'svg' 'canvas' 'html', // 가능한 svg로 쓰면 될듯 (canvas로 하면 css 처리법도 다르고, 적용 안되는 효과도 있는데 개발자도구에서 소스 변경되는 게 노출이 안됨, html은 잘 안쓰는 듯 근데 생략해도 잘 나오네)
      },
      animationSpeed: 1,
    };
  },
  mounted () {
    console.log(this.anim);
  },
  methods: {
    handleAnimation(anim) {
      this.anim = anim;
    },

    stop() {
      this.anim.stop();
    },

    play() {
      this.anim.play();
    },

    pause() {
      this.anim.pause();
    },

    onSpeedChange() {
      this.anim.setSpeed(this.animationSpeed);
    },
  },
};
</script>
