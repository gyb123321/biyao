<template>
	<view class="box">
		<ul>
			<scroll-view :scroll-top="bian" scroll-y="true" scroll-with-animation="true" class="scroll-Y">
				<li @click="jk(item,$event)" key="index" v-for="item in title" :class="name==item? 'box1':'' ">
					{{item}}
				</li>
			</scroll-view>
		</ul>
		<view class="cv">
			<view class="biaoti">{{name}}</view>
		</view>
		<view class="litia">
			<ul class="dong">
				<block key="index" v-for="(item,index) in mz">
					<li v-if="index<4">
						<view class="mingzi">
							{{item}}
						</view>
						<view class="nihao">
								<view key="index" v-for="(item1,index) in wupin[index]" class="wupi">
							<img class="fule" v-if="index<5" :src="item1.imageUrl" alt="">
							<p v-if="index<5">{{item1.title}}</p>
						</view>
						</view>
					
					</li>
				</block>
			</ul>
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
	let name = ref("个护")
	let bian = ref("")
	let mz = ref([])
	var zhi = []
	var er = []
	var bawo = []
	let wupin = ref([])
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
			url: '/api/getTypeTwo?type_one=' + name.value, //仅为示例，并非真实接口地址。
			header: {
				'custom-header': 'hello' //自定义请求头信息
			},
			success: (res) => {
				zhi = res.data
				mz.value = res.data
				zhi.forEach((item, index) => {
					if (index < 4) {
						uni.request({
							url: '/api/getTypeTwoList?type_one=' + name.value + "&" +
								"type_two=" + item,
							header: {
								'custom-header': 'hello' //自定义请求头信息
							},
							success: (res) => {
								wupin.value.push((res.data))
							},
						});
					}
				})
			},
		});
	})
	let jk = (x, event) => {
		wupin.value = []
		if (x == "个护") {
			name.value = x
			bian.value = 0
		} else {
			name.value = x
			bian.value = event.layerY
		}

		uni.request({
			url: '/api/getTypeTwo?type_one=' + name.value, //仅为示例，并非真实接口地址。
			header: {
				'custom-header': 'hello' //自定义请求头信息
			},
			success: (res) => {
				zhi = res.data
				mz.value = res.data
				console.log(zhi);
				zhi.forEach((item, index) => {
					if (index < 4) {
						uni.request({
							url: '/api/getTypeTwoList?type_one=' + name.value + "&" +
								"type_two=" + item,
							header: {
								'custom-header': 'hello' //自定义请求头信息
							},
							success: (res) => {
								wupin.value.push(res.data)
								console.log(wupin.value);
							},
						});
					}


				})
			},
		});


	}
</script>

<style>
	p{
		width: 160rpx;
		font-size: 15rpx;
	}
	.nihao{
		display: flex;
		flex-wrap: wrap;
	}
	.wupi {
		float: left;
	}

	.fule {
		width: 100px;
	}

	.dong {
		margin-top: 40px;
		list-style: none;
		width: 100%;
	}

	.litia {
		float: left;
		width: 200px;
	}

	.cv {
		position: absolute;
		top: 48rpx;
		left: 376rpx;
	}

	.scroll-Y {
		height: 1200rpx;
	}

	ul {
		padding: 0;
		width: 150rpx;
		position: relative;
		float: left;
	}

	.scroll-Y li {
		text-align: center;
		height: 40px;
		list-style: none;
		margin-top:
			30rpx;
		line-height: 40px;
	}

	.box1 {
		border-left: 1px solid rebeccapurple;
		color: rebeccapurple;
	}
</style>