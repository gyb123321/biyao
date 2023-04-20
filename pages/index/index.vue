<template>
	<view class="content">
		<view class="box">
			<view class="imgs">
				<view class="header-price">
					50元
				</view>
				<view class="header-right">
					<p>123</p>
					<p class="bottom-p">下载app领取新用户限量专属特权</p>
				</view>
			</view>

		</view>
		<view class="home-top-section">
			<view class="home-top">
				<view class="search-input-container">
					<view class="search-input">
						<view @click="gh" class="searchIcon">
							请输入您想要的商品
						</view>
					</view>
				</view>
			</view>
			<view class="jk">
				<ul @click="cao" :class="fale? 'box1' :'box2'">
					<li class="lis">热门</li>
					<li class="lis" v-for="(item,index) in title">{{item}}</li>
				</ul>
			</view>
		</view>
		<view class="da">
			<swiper :indicator-dots="true" :autoplay="true" :circular="true" :interval="3000" :duration="1000">
				<swiper-item v-for="(item,index) in arr">
					<img class="imges" :src="item" alt="">
				</swiper-item>
			</swiper>
		</view>
		<div data-v-bf7bb9e2="" class="home-characteristic">
			<ul class="hh">
				<li data-v-bf7bb9e2="">大牌品质</li>
				<li data-v-bf7bb9e2="">/</li>
				<li data-v-bf7bb9e2="">工厂价格</li>
				<li data-v-bf7bb9e2="">/</li>
				<li data-v-bf7bb9e2="">分期支付</li>
				<li data-v-bf7bb9e2="">/</li>
				<li data-v-bf7bb9e2="">顺丰包邮</li>
				<li data-v-bf7bb9e2="">/</li>
				<li data-v-bf7bb9e2="">无忧退款</li>
			</ul>
		</div>
		<div data-v-0b400fe2="" data-v-bf7bb9e2="" class="home-operational">
			<ul data-v-0b400fe2="">
				<li data-v-0b400fe2=""><img data-v-0b400fe2=""
						src="http://bfs.biyao.com/group1/M01/87/05/rBACVF9I-oCADPIbAAAW-6wj7Nk477.png"
						class="home-operational-icon">
					<p data-v-0b400fe2="">品质男装</p> <!----> <!----> <!----> <img data-v-0b400fe2=""
						src="http://bfs.biyao.com/group1/M01/88/EF/rBACW19I-HCAOSpnAAAGpZDfRyc322.png"
						class="home-operational-point">
				</li>
				<li data-v-0b400fe2=""><img data-v-0b400fe2=""
						src="http://bfs.biyao.com/group2/M00/7D/E0/CghkFmMV0NGAKS9iAAAYBi-yE7E858.png"
						class="home-operational-icon">
					<p data-v-0b400fe2="">食品饮料</p> <!----> <!----> <!----> <!---->
				</li>
				<li data-v-0b400fe2=""><img data-v-0b400fe2=""
						src="http://bfs.biyao.com/group1/M01/87/03/rBACVF9I-RmAHwqQAAATob9apjA195.png"
						class="home-operational-icon">
					<p data-v-0b400fe2="">每日签到</p> <!----> <!----> <!----> <img data-v-0b400fe2=""
						src="http://bfs.biyao.com/group1/M01/88/F0/rBACW19I-W2AcPpeAAAIa2fU6MM732.png"
						class="home-operational-point">
				</li>
				<li data-v-0b400fe2=""><img data-v-0b400fe2=""
						src="http://bfs.biyao.com/group1/M01/88/F0/rBACW19I-daAfvjvAAAXEsKWt18728.png"
						class="home-operational-icon">
					<p data-v-0b400fe2="">每日上新</p> <!----> <!----> <!---->
				</li>
				<li data-v-0b400fe2=""><img data-v-0b400fe2=""
						src="http://bfs.biyao.com/group1/M01/88/F1/rBACW19I-hCAXKHlAAAStrCj5PY962.png"
						class="home-operational-icon">
					<p data-v-0b400fe2="">生鲜直供</p> <!----> <!----> <!----> <!---->
				</li>
			</ul>
		</div>
		<view class="recommend-wrap">
			<view class="kong"></view>
			<view class="nb" v-if="fles">
				<template key="index" v-for="(item,index) in isarr">
					<view @click="id(item.Id)" key="index"  v-for="(item,index) in isarr[index]">
						<img class="ngm" :src="item.imageUrl" alt="">
						<p>￥{{item.priceStr}}
							<span class="lan">{{jing[index]}}</span>
							<span class="hong" v-if="index>3">{{pin[index]}}</span>
							<span class="hong" v-if="index <3">{{pin[index]}}</span>
						<p class="mingcheng">{{item.title}}</p>
						</p>
						<p class="zhiyin">{{item.evaluate}}条好评</p>
					</view>
				</template>
			</view>
		</view>
	</view>
</template>

<script setup>
	import {
		ref
	} from 'vue'
	import {
		onReady,
		onLoad,
		onReachBottom,
	} from '@dcloudio/uni-app'
	let title = ref([])
	let fale = ref(true)
	let arr = ref(["https://bfs.biyao.com/group2/M00/41/88/CghiFmKUPDuAOJwXAABclpmxKME954.jpg",
		"https://bfs.biyao.com/group2/M00/31/60/CghjFmJ4eCCATQmYAABXmtU9ykY290.jpg",
		"https://bfs.biyao.com/group2/M00/34/22/CghiFmJ8waKABI_PAABHDMTIEcY173.jpg",
		"https://bfs.biyao.com/group2/M00/39/A4/CghkFmKF-UiAOJdMAABPdmuHoyA590.jpg",
		"https://bfs.biyao.com/group2/M00/42/66/CghjFmKVp3CASWQ3AABKXcn0qLI790.jpg",
	])
	let isarr = ref([])
	let jing = ref([])
	let pin = ref([])
	var shu = 1
	var ji = []
	let fles = ref(true)
	onLoad(() => {
		uni.request({
			url: '/api/getTypeOne', //仅为示例，并非真实接口地址。
			header: {
				'custom-header': 'hello' //自定义请求头信息
			},
			success: (res) => {
				console.log(res.data);
				title.value = res.data
			}
		});
		uni.request({
			url: '/api/hotList?page=' + shu,
			header: {
				'custom-header': 'hello'
			},
			success: (res) => {
				ji.push(res.data)
				isarr.value = ji
				console.log(isarr.value);
				for (let i = 0; i < isarr.value.length; i++) {
					for (let s = 0; s < isarr.value[i].length-1; s++) {
						   if(isarr.value[i][s].labels.split(":").length==5){
							   jing.value.push(isarr.value[i][s].labels.split(":")[4].split('"')[1]);
						   }else{
							    pin.value.push(isarr.value[i][s].labels.split(":")[8].split('"')[1]);
								 jing.value.push(isarr.value[i][s].labels.split(":")[4].split('"')[1]);
						   }
						

						 
					}
					
				}
				console.log(jing.value);
			}
		});

	})
	onReady(() => {

	})
	let cao = () => {
		fale.value = !fale.value
	}

	let id = (x) => {
		console.log(x);
	}
	onReachBottom(() => {
		shu++
		uni.request({
			url: '/api/hotList?page=' + shu,
			header: {
				'custom-header': 'hello'
			},
			success: (res) => {
				ji.push(res.data)
				isarr.value = ji
				console.log(isarr.value);
				fles.value = false
				fles.value = true
				// for (let i = 0; i < isarr.value.length; i++) {
				// 	jing.value.push(isarr.value[i].labels.split(":")[4].split('"')[1]);
				// 	if (i == 3) {
				// 	} else {
				// 		pin.value.push(isarr.value[i].labels.split(":")[8].split('"')[1]);
				// 	}

				// }
			}
		});
	
	})
	let gh=()=>{
		console.log(321);
	}
</script>

<style>
	.zhiyin {
		font-size: 15rpx;
		color: #666 !important;
	}

	.mingcheng {
		font-size: 15rpx;
		color: #666 !important;
	}

	.hong {
		background: rgb(255, 255, 255);
		color: rgb(251, 76, 129);
		border: 0.015rem solid rgb(251, 76, 129);
		border-radius: 2px;
		display: inline-block;
		margin-left: 10rpx;
	}

	.lan {
		background: rgb(171, 127, 209);
		color: rgb(255, 255, 255);
		border: 0.015rem solid rgb(171, 127, 209);
		border-radius: 2px;
		display: inline-block;
	}

	.nb p {
		color: #f7a701;
		height: 100rpx;
	}

	.ngm {
		width: 370rpx;
		height: 370rpx;
	}

	.nb {
		display: flex;
		flex-wrap: wrap;
		justify-content: space-between;
	}

	.kong {
		width: 100%;
		height: 40rpx;
		background: rgb(244, 244, 244);

	}

	.home-operational ul li .home-operational-point {
		display: block;
		position: absolute;
		top: 0.1rem;
		left: 0.12rem;
		width: 3.2rem;
		height: 1.3rem
	}

	.home-operational ul li p {

		font-size: 10rpx;
		text-align: center;
		height: 1.24rem;
		line-height: 0.24rem;
		color: #666;
		width: 3.2rem;
		padding: 0rem 0.12rem;
		overflow: hidden;
		white-space: nowrap;
		text-overflow: ellipsis;
		margin-top: 5rpx;
		line-height: 1.24rem;
	}

	.home-operational ul li .home-operational-icon {
		width: 80rpx;
		height: 80rpx;
		display: block;
		margin: 0 auto 0.08rem;
	}

	.home-operational ul li {
		width: 100rpx;
		overflow: hidden;
		position: relative;
		padding-top: 0.32rem;
		margin-top: 0.1rem;
	}

	.home-operational ul {

		display: flex;

		justify-content: space-around;
	}

	.home-operational {
		padding: 0.15rem 0.15rem 0.25rem;
		background: #ffffff;
	}

	.hh li {
		float: left;
	}

	.hh {
		width: 100vw;
		display: flex;
		justify-content: space-around;
	}

	.home-characteristic {
		margin-top: 10rpx;
		height: 0.72rem;
		width: 7.5rem;
		font-size: 0.24rem;
		color: #9687a4;
		background: #fff;
		line-height: 0.72rem;
	}

	.imges {
		height: 100%;
		width: 100%;
	}

	.lis {
		margin-left: 20px;
		float: left;
	}

	li {
		list-style: none;
	}

	.searchIcon {
		font-family: PingFangSC-Regular;
		font-size: 0.28rem;
		color: #bbb;
	}

	.search-input {
		width: 92%;
		height: 70rpx;
		margin: 0 auto;
		background: #f4f4f4;
		border-radius: 40rpx;
		overflow: hidden;
		display: -webkit-box;
		display: -webkit-flex;
		display: flex;
		-webkit-box-pack: start;
		-webkit-justify-content: flex-start;
		justify-content: flex-start;
		-webkit-box-align: center;
		-webkit-align-items: center;
		align-items: center;
	}

	.imgs {
		height: 100rpx;
		background-image: url("https://bfs.biyao.com/group1/M00/B4/3B/rBACW1yjqW6Ae7RhAAAd5r4TJxY228.jpg");
		background-repeat: no-repeat;
		background-position: 94% 14%;
		background-size: 750rpx, 100vh;
		display: flex;
	}

	.header-price {
		height: 100%;
		line-height: 40px;
		margin: 0.21rem 0rem;
		padding: 0rem 0.32rem;
		font-family: PingFangSC-Medium;
		font-size: 30rpx;
		color: #fff;
		text-align: center;
		border-right: #fff solid 0.01rem;
	}

	.bottom-p {
		line-height: 36rpx;
		margin: 0.21rem 0rem;
		padding: 0rem 0.32rem;
		font-family: PingFangSC-Medium;
		font-size: 10rpx;
		color: #fff;
		text-align: center;
	}

	.search-input-container {
		width: 100%;
		background: #fff;
		padding-top: 0.2rem;
		padding-bottom: 0.12rem;
	}

	.box1 {
		height: 40rpx;
		float: left;
		padding: 0;
		overflow: hidden;
		transition: all 1s;
		position: absolute;
		top: 0;
		z-index: 100;
		background-color: #ffffff;
		margin-top: 20rpx;
	}

	.box2 {
		height: 250rpx;
		float: left;
		overflow: hidden;
		padding: 0;
		transition: all 1s;
		position: absolute;
		top: 0;
		z-index: 100;
		background-color: #ffffff;
		margin-top: 20rpx;
	}

	ul {
		padding: 0;
	}

	.jk {
		position: relative;
	}

	.da {
		margin-top: 80rpx;
	}
</style>