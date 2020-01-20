<template>
	<div>
		<div class="banner">
			<svg class="Zi Zi--Star" fill="currentColor" viewBox="0 0 24 24" width="36" height="36" style="color: #0084FF; margin-right: 10px;">
				<path
					d="M5.515 19.64l.918-5.355-3.89-3.792c-.926-.902-.639-1.784.64-1.97L8.56 7.74l2.404-4.871c.572-1.16 1.5-1.16 2.072 0L15.44 7.74l5.377.782c1.28.186 1.566 1.068.64 1.97l-3.89 3.793.918 5.354c.219 1.274-.532 1.82-1.676 1.218L12 18.33l-4.808 2.528c-1.145.602-1.896.056-1.677-1.218z"
					fill-rule="evenodd"
				></path>
			</svg>
			<h2>热门收藏夹</h2>
		</div>
		<div class="container">
			<div class="row" v-for="(item, index) in favorites" v-if="index > begin && index < end" :key="index">
				<div class="col-4">
					<h3>{{ item.title }}</h3>
					<!-- <div><img :src="item.creatorAvatar" alt="" /></div> -->
					<h5>{{ item.creatorName }} 创建</h5>
					<div>
						<div class="r"><button class="btn">关注专题</button>
						{{ item.followers }}人关注
					</div>
					</div>
				</div>
				<div class="col-8">
					<h3>{{ item.questionTitle }}</h3>
					<p>{{ item.answerAuthorName }}：{{ item.answerContent }}</p>
					<p>回答{{ item.voteUpCount }},{{ item.commentCount }}评论</p>
					<p>已收藏{{ item.tatalCount }}内容 ></p>
				</div>
			</div>
		</div>
		<button @click="showAll" class="flex center btn">展开全部</button>
		<button>
			<a href="#" style="position: fixed; bottom: 5%; right: 2%; c"><i class="iconfont">&#xe604;</i></a>
		</button>
	</div>
</template>

<script>
export default {
	name: 'favorite',
	data() {
		return {
			favorites: [],
			begin: 0,
			end: 8
		};
	},
	created() {
		this.axios.get('http://localhost:8080/api/favorite/all').then(res => {
			console.log(res);
			this.favorites = res.data.data;
		});
	},
	methods: {
		showAll() {
			this.begin = 0;
			this.end = this.favorites.length;
		}
	}
};
</script>

<style lang="scss" scoped>
.banner {
	width: 100%;
	background-color: #ffffff;
	margin-bottom: 10px;
	margin-top: -10px;
	height: 100px;
	border: 1px solid #dddddd;
	box-shadow: 2px 5px 5px #ddd;
	padding-left: 10%;
	display: flex;
	align-items: center;
	img {
		height: 60%;
	}
}
.meta {
	margin-top: -30px;
}
.container {
	background-color: #ffffff;
	.row {
		display: flex;
		margin-bottom: 10px;
		border: 1px solid #d6d6d6;
		border-radius: 4px;
		height: 200px;
		padding: 14px;
		box-shadow: 0 1px 3px 0 rgba(26, 26, 26, 0.1);
		.col-4 {
			flex: 0 0 33%;
			height: 100%;
			img {
				width: 90%;
				height: 100%;
				border-radius: 5px;
			}
		}
	}
}
.section {
	padding: 0 8px;
	height: 24px;
	line-height: 24px;
	border-radius: 5px;
	background-color: #f6f6f6;
	color: #8590a6;
	font-size: 12px;
	margin-left: 10px;
}
.iconfont {
	font-size: 30px;
	color: dodgerblue;
}
.r {
	
}
.btn {
	-webkit-tap-highli0ht-color: rgba(26, 26, 26, 0);
	font: inherit;
	cursor: pointer;
	background: none;
	border: none;
	outline: none;
	-webkit-appearance: none;
	height: 34px;
	border-radius: 3px;
	font-size: 14px;
	font-weight: 600;
	width: 102px;
	color: #0084ff;
	background-color: rgba(0, 132, 255, 0.08);
}
.center {
	color: #333333;
	background-color: #ffffff;
	width: 60px;
	height: 50px;
	border-radius: 47%;
}
.introduction {
	margin-top: -10px;
}
// img {
// 	width: 20%;
// 	height: 10%;
// }
</style>
