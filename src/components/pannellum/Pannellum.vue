<template>
    <div class="pannellum" @click="getValue($event)">
        <VPannellumn
            :src="equirectangularUrl"
            :showFullscreen="true"
            :showZoom="true"
            :compass="true"
        >
        </VPannellumn>
        <div class="click" @click="changeImg($event)">点击</div>ß
    </div>
</template>
<script>
export default {
  data () {
    return {
      equirectangularUrl: require('../../assets/images/1.jpg'),
      num: 1
    };
  },
  methods: {
    changeImg () {
      this.num++;
      this.equirectangularUrl = require(`../../assets/images/${this.num}.jpg`);
    },
    // 获取坐标
    getValue (e) {
      console.log(e)
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
