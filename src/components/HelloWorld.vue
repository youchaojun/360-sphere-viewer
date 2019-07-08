<template>
    <div>
        <div class="PSViewer" ref="psvdbg" v-if="show">
            <div class="control" @click="changeImage">控制按钮</div>
        </div>
    </div>
</template>

<script>
import PhotoSphereViewer from 'photo-sphere-viewer';
import 'photo-sphere-viewer/dist/photo-sphere-viewer.css';
export default {
  name: 'PSViewer',

  data () {
    return {
      width: 798,
      height: 498,
      img: require('../assets/images/1.jpg'),
      show: true,
      PSV: true,
      imgNum: 1
    };
  },

  beforeDestory () {},

  mounted () {
    this.initPhotoSphere();
  },

  methods: {
    initPhotoSphere () {
      this.PSV = new PhotoSphereViewer({
        panorama: this.img, // Container
        container: this.$refs.psvdbg, // Deactivate the animation
        time_anim: false, // Display the navigation bar // navbar: true,
        navbar: ['autorotate', 'zoom', 'fullscreen'],
        navbar_style: {
          backgroundColor: 'rgba(58,67,77,0.7)'
        }, // Resize the panorama
        size: {
          width: '100%',
          height: '498px'
        }
      });
    },
    // 点击更换图片
    changeImage () {
      this.imgNum++;
      if (this.imgNum === 6) {
        this.imgNum = 1;
      }
      this.img = require(`../assets/images/${this.imgNum}.jpg`);
      if (this.PSV) {
        this.PSV.destroy();
      }
      this.$nextTick(() => {
        this.initPhotoSphere();
      });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.PSViewer {
    width: 1000px;
    height: 800px;
    position: relative;
    z-index: 1;
}
.control {
    width: 100px;
    height: 100px;
    background: red;
    position: absolute;
    top: 20px;
    z-index: 200;
}
</style>
