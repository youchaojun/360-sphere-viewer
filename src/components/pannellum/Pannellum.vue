<template>
    <div class="pannellum" @click="getValue($event)">
        <VPannellumn
            :src="equirectangularUrl"
            :showFullscreen="true"
            :showZoom="true"
            :compass="true"
            :yaw="gamma"
            :pitch="beta"
        ></VPannellumn>
        <div class="click" @click="changeImg($event)">点击</div>
    </div>
</template>
<script>
export default {
  data () {
    return {
      equirectangularUrl: require('../../assets/images/1.jpg'),
      num: 1,
      gamma: 0,
      beta: 0
    };
  },
  mounted () {
    window.addEventListener('deviceorientation', this.orientationHandler, false);
  },
  methods: {
    changeImg () {
      this.num++;
      this.equirectangularUrl = require(`../../assets/images/${this.num}.jpg`);
    },
    // 获取坐标
    getValue (e) {
      console.log(e);
    },
    orientationHandler (event) {
      console.log(event);

      this.gamma = Math.round(event.gamma);
      this.beta = Math.round(event.beta);
    }
  }
};
</script>
<style lang="scss" scoped>
.pannellum {
    width: 100%;
    height: 600px;
    position: relative;
    /* v::deep .pnlm-container { */
    .click {
        color: green;
        background: #fff;
        position: absolute;
        top: 100px;
        left: 200px;
        /* z-index: 999; */
    }
    /* } */
}
</style>
