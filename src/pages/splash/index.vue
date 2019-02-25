<template>
  <div class="container">
    <swiper class="splash" indicator-dots>
      <swiper-item class="sw-item" v-for="(item,index) in splash" :key="index">
        <image :src="item.image" class="slide-image" mode="aspectFill"/>
        <button class="start" v-if="index == count-1" @tap="board">立刻体验</button>
      </swiper-item>
    </swiper>
  </div>
</template>

<script>
import bmall from '../../utils/bmall.js'
export default {
  data () {
    return {
      splash: [
        // {image:'',id:xx}
      ],
      count:4
    }
  },

  components: {
  },

  methods: {
    board(){
      mpvue.setStorageSync('splash_bmall',true);

      mpvue.switchTab({
        url: '/pages/board/main'
      });

    },
  },

  created () {
    // let app = getApp()
  },

  onLoad () {

    let value = mpvue.getStorageSync('splash_bmall')

    if (value) {
      mpvue.switchTab({
        url: '/pages/board/main'
      })
      return;
    }

    bmall({
      url: '/index/listFocus?1546824341870',
      data: {
        start:1,
        count:this.count
      }
    }).then(
      res=>{
        if (!res.data.data) return;
        let result = [];
        res.data.data.map((item) => {
          result.push({
            image: item.picUrl,
            id: item.id
          })
        });
        this.splash=result;
      }
    )
  }
}
</script>

<style scoped>
.container {
  height: 100%;
  overflow: hidden;
}

.splash {
  height: 100%;
}

.splash sw-item {
  flex: 1;
}

.splash .slide-image {
  position: absolute;
  height: 100%;
  width: 100%;
  opacity: 0.9;
}

.start {
  position: absolute;
  bottom: 200rpx;
  left: 50%;
  width: 300rpx;
  margin-left: -150rpx;
  background-color: rgba(53, 73, 94, 0.4);
  color: #fff;
  border: 5rpx solid #35495e;
  font-size: 40rpx;
}
</style>
