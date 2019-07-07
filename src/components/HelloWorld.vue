<template>
    <div>
        <div class="PSViewer" ref="psvdbg">
        </div>
          <div class="control" @click="changeImage">控制按钮</div>
    </div>
</template>

<script>
var THREE = require("three");
var PhotoSphereViewer = require("photo-sphere-viewer");
import 'photo-sphere-viewer/dist/photo-sphere-viewer.css'
export default {
    name: "PSViewer",

    data() {
        return {
            width: 798,
            height: 498,
            img: require("../assets/images/1.jpeg")
        };
    },

    beforeDestory() {},

    mounted() {
        this.init();
    },

    methods: {
        // photo-sphere-viewer
        init: function() {
            const self = this;

            var PSV = new PhotoSphereViewer({
                // Panorama, given in base 64
                panorama: self.img, // Container

                container: self.$refs.psvdbg, // Deactivate the animation

                time_anim: false, // Display the navigation bar // navbar: true,

                navbar: ["autorotate", "zoom", "fullscreen"],
                navbar_style: {
                    backgroundColor: "rgba(58,67,77,0.7)"
                }, // Resize the panorama

                size: {
                    width: "100%",
                    height: "498px"
                }
            });
        },
        // 点击更换图片
        changeImage () {
          
          this.img = require('../assets/images/sun.jpg')
        }
    }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .PSViewer{
    width: 1000px;
    height: 800px;
    position: relative;
    z-index: 1;
  }
  .control{
    width: 100px;
    height: 100px;
    background: red;
    position: absolute;
    top: 20px;
    z-index: 10;
  }
</style>
