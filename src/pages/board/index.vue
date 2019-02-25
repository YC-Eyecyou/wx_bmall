<template>
  
  <div class="container">
  	<div class="slide">
  		<swiper class='swp' :indicator-dots="true" :autoplay="true" :interval="1000" :duration="100" :circular="true">
  			<swiper-item
  				v-for="item of banner.content"
  				:key="item.id"
  			>
  				<navigator :url="'../item/main?id='+item.id">
  					<image class='nav-img' :src="item.image" mode="aspectFill"/>
  				</navigator>
  			</swiper-item>
  		</swiper>
  	</div>
  	<div class="board" :scroll-y="true">
  		<navigator 
  			v-for="item in list"
  			:key="item.key"
  			:url="'../list/main?key='+item.key+'&title='+item.title"
  		>
  			<div class="board-item">
  				<span class="board-item-title">{{item.title}}</span>
  				<img class="arrow" :src="item.iconUrl"/>
  			</div>
  		</navigator>
  	</div>
  </div>

</template>

<script>
import douban from '../../utils/douban.js';
import bmall from '../../utils/bmall.js';
export default {
  data () {
    return {
      banner: {
        key: '/index/listFocus?1546824341870',
        title: '正在热销',
        count:4,
        content: [
          // {image:'',id:xx}
        ]
      },
      list: [
        { key: 'in_theaters', title: '魔兽世界', iconUrl:'/static/images/wow.png' },
        { key: 'top250', title: '守望先锋', iconUrl:'/static/images/ow.png' },
        { key: 'coming_soon', title: '炉石传说', iconUrl:'/static/images/ls.png' },
				{ key: 'in_theaters', title: '暗黑破坏神', iconUrl:'/static/images/d.png' },
				{ key: 'in_theaters', title: '星际争霸2', iconUrl:'/static/images/sc.png' },
				{ key: 'in_theaters', title: '风暴英雄', iconUrl:'/static/images/fb.png' },
				{ key: 'in_theaters', title: '暴雪游戏', iconUrl:'/static/images/blz.png' }
      ]
    }
  },
	
  components: {
  },

  methods: {
    
  },

  created () {
    // let app = getApp() 抓
    bmall({
      url: this.banner.key,
      data: { count: this.banner.count }
    }).then(
      res => {
        
        if (!res.data.data) return;
        let result = [];
        res.data.data.map((item) => {
          result.push({
            image: item.picUrl,
            id: item.id
          })
        });
        // console.log(result);
        this.banner.content=result;
        /* this.setData({
          'banner.content': result
        }); */
        // console.log(this.banner.content);
      }
    )
  }
}
</script>

<style scoped>
.container {
  display: flex;
  flex: 1;
  flex-direction: column;
  box-sizing: border-box;
}

.slide .swp {
  height: 400rpx;
}

.slide .nav-img {
  height: 400rpx;
  width: 100%;
}

.board {
  display: flex;
  flex: 1;
  flex-direction: column;
}


.board-item {
  display: flex;
  cursor: pointer;
  border: 5rpx solid #264770;
  margin: 40rpx;
  padding: 40rpx;
	background:#012a60;
	color:#fff;
}

.board-item .board-item-title {
  flex: 1;
}

.board-item .arrow {
  height: 40rpx;
  width: 40rpx;
} 
</style>
