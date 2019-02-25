<template>
  <div class="item">
	<div class="productPic">
		<img class="poster" :src="item.image"/>
	</div>
	<div class="meta">
		<span class="title">{{item.title}}</span>
		<!-- <span class="sub-title">2222222222222</span> -->
		<!-- <div class="artists">导演<block> 333333333333 </block></div> -->
	</div>
	<div class="price">
		<span class='rating'>{{item.average}}</span>
	</div>
  </div>
</template>

<script>
export default {
  props: ['item']
}
</script>

<style scoped>

.item {
  /* display: flex;
  padding: 20rpx 40rpx;
  border-bottom: 1rpx solid #eee;
  cursor: pointer; */
  min-height: 4.76rem;
  width: 100%;
  text-align: center;
  background: #fff;
}

.item .productPic{
	height: 3.4rem;
    padding-top: .2rem;
    position: relative;
}

 .item .poster {
  /* width: 128rpx;
  height: 168rpx;
  margin-right: 20rpx; */
	width: 3rem;
    height: 3rem;
    display: block;
    margin: 0 auto;
}

 /* .item .meta {
  flex: 1;
} */

 .item .meta .title,
 .item .meta .sub-title {
    line-height: .4rem;
    color: #333;
    font-size: .28rem;
    padding: 0 .26rem;
    text-align: left;
}

 /* .item .meta .title {
  font-size: 32rpx;
} */

/* .item .meta .sub-title {
  font-size: 22rpx;
  color: #c0c0c0;
} */

 .item .meta .artists {
  font-size: 24rpx;
  color: #999;
}

 .item .price {
	
	font-size: 0;
    line-height: .4rem;
    margin-top: .14rem;
    padding-left: .22rem;
    text-align: left;
 }

 .item .rating {
  /* display: inline-block;
  width: 40rpx;
  font-size: 28rpx;
  font-weight: bold;
  span-align: center;
  background-color: rgba(247, 76, 49, 0.8);
  color: #fff;
  padding: 10rpx;
  border-radius: 20rpx; */
  font-size: .28rem;
  line-height: .4rem;
  color: #e60012;
}
</style>
