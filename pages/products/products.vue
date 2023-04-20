<template>
	<view class="box">
		<view class="box1">
			<swiper class="box11">
				<template key="index" v-for="(item,index) in imgs">
					<swiper-item class="box111">
						<image :src="item" mode=""></image>
						<text>{{index+1}}/6</text>
					</swiper-item>
				</template>
			</swiper>
		</view>
		<view class="box2">
			<view class="b21">
				<div class="b21d4">
					<div class="b21d1">￥{{arr.priceStr}}</div>
					<div class="b21d2">
						<!-- <span></span>  -->
						支持花呗分期付款
					</div>
				</div>

				<div class="b21d3">收藏</div>
			</view>
			<view class="b22">
				<div class="b221">{{arr.supplier}}</div>
				<div class="b222">生命周期:{{arr.leadTime}}天</div>
			</view>
			<view class="b23">
				{{arr.title}}
			</view>
			<view class="b24">
				{{arr.salePoint}}
			</view>
			<view class="b25">
				<div><span></span>七天无理由退货</div>
				<div><span></span>先行赔付</div>
				<div><span></span>超时赔偿</div>
				<div><span></span>顺丰包邮</div>
				<div></div>
			</view>
		</view>
		<view class="box3">
			<swiper vertical circular autoplay interval="3000">
				<swiper-item key="index" v-for="(item,index) in buarr">
					<view class="box31">
						<div class="b311"><img
								src="https://static.biyao.com/mnew/img/master/firendHelp/rightsDetail/icon_mysterious_friend_big@2x_54bfa3c.png"
								alt="">
							<span>{{item.name1}}</span>
						</div>
						<div class="box32">
							<div>
								<p>还差<span>1</span>人拼成</p>
								<p class="p1">剩余:03:06:40</p>
							</div>
							<span class="bu1">参团</span>
						</div>
					</view>
					<view>
						<div class="b311"><img
								src="https://static.biyao.com/mnew/img/master/firendHelp/rightsDetail/icon_mysterious_friend_big@2x_54bfa3c.png"
								alt="">
							<span>{{item.name2}}</span>
						</div>
						<div class="box32">
							<div>
								<p>还差<span>1</span>人拼成</p>
								<p class="p1">剩余:03:06:40</p>
							</div>
							<span class="bu1">参团</span>
						</div>

					</view>
				</swiper-item>
			</swiper>
		</view>
		<view class="view3">
			<view class="">
				<span>拼团玩法</span><span>详细规则 ></span>
			</view>
			<image src="https://static.biyao.com/mnew/img/master/togetherGroup/rule@2x_4b87758.png" mode=""></image>
		</view>
		<view class="box4">
			<view class="b4v1">
				<span>商品评价({{this.plarr.length/12}})</span><span>好评率:99.8% ></span>

			</view>
			<view class="b4v2">
				<view class="v2v1">
					<div> <img :src="plarr[3]" alt="">
						<p>{{plarr[1]}}</p>
						<span>{{plarr[11]}}</span>
					</div>
					<div><span></span>
						<span>满意</span>
					</div>
				</view>
				<view class="v2v2">
					{{plarr[7]}}{{plarr[9]}}
				</view>
				<view class="v2v3">
					{{plarr[5]}}
				</view>
			</view>
		</view>
		<view class="box5">
			<view class="b5v1">
				<div class="d51d1">
					<img :src="arr.addressLogo" alt="">
					<div class="d1d1">
						<p>{{arr.supplier }}</p>
						<p>
							<span>商品质量:5.0</span>
							<span>服务态度:5.0</span>
						</p>
					</div>
				</div>
				<div class="d51d2">全部商品 ></div>
			</view>
			<scroll-view scroll-x class="b5v2">
				<view class="b5b5">
					<div class="b5v2div" key="index" v-for="(item,index) in jdkk">
						<img :src="item.imageUrl" alt="">
						<p class="pp1">{{item.title}}</p>
						<p class="pp2">一起拼</p>
						<p class="pp3">￥{{item.priceStr}}</p>
					</div>
				</view>

			</scroll-view>
		</view>
		<view class="box6">
			<view class="">
				<span class="s1">品牌</span><span class="s2">{{arr.supplier}}</span>
			</view>
			<view class="">
				<span class="s1">产品名称</span><span class="s2">{{arr.title}}</span>
			</view>
			<view class="">
				<span class="s1">产品特点</span><span class="s2">{{arr.salePoint}}</span>
			</view>
			<view class="b6v2">
				展示全部
			</view>
		</view>
		<view class="box7">
			<image key="index" v-for="(item,index) in imgs1" :src="item" mode=""></image>
		</view>
		<view class="box8">
			<view class="">
				<span>《用户服务协议》</span>|<span> 《隐私政策》</span>
			</view>
			<view class="">

				必要商城提示您，产品“由某制造商出品”仅为陈述制造商既往生产经历，并不意味着相应产品与特定品牌产品相同或近似。

			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				arr: [],
				buarr: [{
					name1: "小明",
					name2: "小红"
				}, {
					name1: "高老师",
					name2: "刘国"
				}, {
					name1: "王开",
					name2: "哇更换"
				}, {
					name1: "小月亮明",
					name2: "fgaga"
				}],
				imgs: [],
				imgs1: [],
				jdkk: [],
				plarr: []
			}
		},
		onLoad(option) {
			console.log(option.id);
			uni.request({
				url: '/api/detail?goodId=' + option.id, //仅为示例，并非真实接口地址。
				success: (res) => {
					console.log(res.data[0]);
					this.arr = res.data[0]
					let l = res.data[0].imgs.split('"')
					for (let i = 0; i < l.length; i++) {
						if (i % 2) {
							this.imgs.push(l[i])
						}
					}
					console.log(this.arr.description);
					let oo = res.data[0].comment.split('"')
					for (let i = 0; i < oo.length; i++) {
						if (i % 2) {
							this.plarr.push(oo[i])
						}
					}
					// console.log(this.plarr);
					let az = res.data[0].description.split("\\n    ")
					console.log(az);
					let al = res.data[0].descriptionImage.split('"')
					for (let i = 0; i < al.length; i++) {
						if (i % 2) {
							this.imgs1.push(al[i])
						}
					}
					console.log(this.imgs1);
					uni.request({
						url: '/api/supplierList?supplier=' + res.data[0].supplier,
						success: (res) => {
							this.jdkk = res.data
							console.log(this.jdkk);
						}
					});

				}
			});
		},
		methods: {

		}
	}
</script>

<style scoped>
	.box1 {
		height: 750rpx;
	}

	.box11 {
		height: 100%;
	}

	.box11 image {
		width: 100%;
		height: 100%;
	}

	.box111 {
		position: relative;
	}

	.box111 text {
		padding: 5rpx 40rpx;
		position: absolute;
		bottom: 20rpx;
		right: 20rpx;
		border-radius: 20px;
		background-color: rgba(0, 0, 0, .3);
		color: #fff;
		z-index: 999;
	}

	.box2 {
		padding: 20rpx;
	}

	.b21 {

		display: flex;
		justify-content: space-between;
	}

	.b21d1 {
		font-size: 44rpx;
		color: #ff3637;
	}

	.b21,
	.b22,
	.b25 {
		display: flex;
	}

	.box3 {
		padding-top: 20rpx;
		padding-bottom: 20rpx;
		box-sizing: border-box;
		background-color: #f4f4f4;
	}

	.box3 view {
		display: flex;
		justify-content: center;
		align-items: center;
		height: 50%;
	}

	.box3 img {
		width: 100rpx;
		height: 100rpx;
		border-radius: 50%;
	}

	.box31 {
		border-bottom: 1px solid #f4f4f4;
	}

	.box3 view {
		display: flex;
		justify-content: space-between;
		align-items: center;
	}

	.box32 {
		display: flex;
		align-items: center;
	}

	.bu1 {
		padding: 10rpx 40rpx;
		background-color: #7F4395;
		color: white;
		margin-right: 20rpx;
	}

	.b311 {
		display: flex;
		align-items: center;
	}

	.box32 div {
		margin: 0px 20px;
	}

	.box32 p span {
		color: #f7a701;
	}

	.p1 {
		font-size: 12spx;
		text-align: right;
	}

	.b21d4 {
		display: flex;
		align-items: center;
	}

	.b21d4 div {
		margin-right: 10rpx;
	}

	.b22 {
		justify-content: space-between;
		margin: 10rpx 0rpx;
	}

	.b221 {
		color: #bf9e6b;
	}

	.b222 {
		color: #bbb;
		font-size: 12px;
	}

	.b23 {
		color: #4a4a4a;
		font-size: 18px;
		margin: 10rpx 0px;
	}

	.b24 {
		color: #999;
		font-size: 13px;
	}

	.b25 {
		display: flex;
		margin-top: 10rpx;
		justify-content: space-between;
		color: #bf9e6b;
		font-size: 12rpx;
		background-color: #FFFBF2;
		align-items: center;
		height: 50rpx;
	}

	.box3 swiper {
		background-color: white;
	}

	.box2 {
		padding-bottom: 0px;
	}

	.view3 {
		padding-bottom: 10rpx;
		background-color: #f4f4f4;
	}

	.view3 view {
		background-color: white;
		display: flex;
		height: 70rpx;
		padding: 10rpx 20rpx;
		align-items: center;
		justify-content: space-between;
	}

	.view3 image {
		width: 100%;
		height: 200rpx;
	}

	.b4v1 {
		display: flex;
		justify-content: space-between;
		padding: 30rpx 20rpx;
	}

	.b4v2 {
		border-top: 1px solid #ebebeb;

	}

	.v2v1 {
		display: flex;
		justify-content: space-between;
	}

	.v2v1 div {
		margin: 10rpx;
		display: flex;
		height: 80rpx;
		align-items: center;
		justify-content: space-between;
	}

	.v2v1 img {
		width: 50rpx;
		height: 50rpx;
		border-radius: 50%;
		margin: 0rpx 10rpx;
	}

	.v2v1 span {
		color: #F7A701;
	}

	.v2v2 {
		padding: 10rpx 20rpx;
		font-size: 24rpx;
		color: #999;
	}

	.v2v3 {
		padding: 10rpx 20rpx;
		font-size: 32rpx;
	}

	.box7 {
		padding: 0px 20rpx;
	}

	.box7 image {
		width: 100%;
		height: 1000rpx;
	}

	.box6 {
		background-color: #EEE;
		padding: 30rpx 20rpx;
	}

	.box6 view {
		padding: 20rpx 0rpx;
		border-bottom: 1px solid #CCC;
	}

	.s1 {
		display: inline-block;
		width: 150rpx;
		color: #828282;
	}

	.b6v2 {
		text-align: center;
		border-bottom: 0px !important;
		color: #9B9B9B;
	}

	.b5v1 {
		display: flex;
		justify-content: space-between;
	}

	.d51d1 {
		display: flex;
		padding: 10rpx 20rpx;
	}

	.d51d1 img {
		width: 100rpx;
		height: 100rpx;
		border: 1px solid #f3f3f3;
		margin-right: 10rpx;
	}

	.d1d1 p {
		margin: 5rpx;
	}

	.d1d1 span {
		color: #bbb;
		font-size: 24rpx;
	}

	.d51d2 {
		display: flex;
		align-items: center;
	}

	.b5b5 {
		display: flex;
	}

	.b5v2div {
		display: inline-block;
		width: 250rpx;
		height: 400rpx;
	}

	.b5v2div img {
		width: 250rpx;
		height: 250rpx;
	}

	.b5v2div p {
		padding: 0px 10rpx;
		white-space: nowrap;
		text-overflow: ellipsis;
	}

	.pp1 {
		color: #4A4A4A;
		font-size: 28rpx;
	}

	.pp2 {
		color: #FB4C81;
		width: 80rpx;
		border-color: #FB4C81;
		border: 1px solid;
		font-size: 28rpx;
		margin-left: 20rpx;
		text-align: center;
	}

	.pp3 {
		color: #F7A701;
		margin: 10rpx 20rpx;
		font-size: 28rpx;
	}

	.box8 view {
		padding: 10rpx 20rpx;
		text-align: center;
		color: #868686;
		font-size: 26rpx;
	}
</style>