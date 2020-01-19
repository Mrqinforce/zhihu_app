<template>
	<div class="container">
		<div class="banner">
			<i class="iconfont">&#xe71f;</i>
			<h3>最新专题</h3>
		</div>
		<div class="row">
			<div class="col-6 card" v-for="(item, index) in specials" :key="index">
				<div><img :src="item.banner" alt="" /></div>
				<div class="card-body">
						<h3>{{ item.title }}</h3>
						<div class="r"><button class="btn">关注专题</button></div>
						<p class="meta">{{ item.updated }}更新,{{ item.viewCount }}次浏览</p>
					<p class="introduction">{{ item.introduction.slice(0, 40) }}...</p>
				</div>
				<span v-for="(section, index) in item.sections" :key="index" class="section">{{ section.sectionTitle }}</span>
			</div>
			<button class="center"><router-link to="/special/all" class="btn" style="color: #AAAAAA;">查看更多专题 ></router-link></button>
		</div>
		<div class="row">
			<div class="banner">
				<i class="iconfont">&#xe630;</i>
				<h3>圆桌讨论</h3>
			</div>
			<div class="col-6 card" v-for="(item, index) in roundTables" :key="index">
				<div class="cards-head">
					<div class="card-background"><img :src="item.banner" alt="" /></div>
					<div class="card-main">
						<p class="name">{{ item.name }}</p>
						<p>{{ item.visitsCount }}人访问,{{ item.includeCount }}人参与</p>
					</div>
					<div class="card-btn"><button class="btn">关注圆桌</button></div>
				</div>
				<div class="card-buttom">
					<span v-for="(section, index) in item.sections" :key="index" class="section">{{ section.sectionTitle }}</span>
				</div>
			</div>
			<button class="center"><router-link to="/roundTable/all" class="btn" style="color: #AAAAAA;">查看更多圆桌 ></router-link></button>
			<button><i class="iconfont" style="position: fixed; bottom: 5%; right: 2%;">&#xe71f;</i></button>
		</div>
		<div class="row">
			<div class="banner">
				<i class="iconfont">&#xe630;</i>
				<h3>热门收藏夹</h3>
			</div>
			<div class="col-6 cards" v-for="(item, index) in favorites" :key="index">
				<div class="card_head">
					<div class="card-body">
						<h3>{{ item.title }}</h3>
						<div class="r"><button class="btn">关注收藏夹</button></div>
						<div><img :src="item.creatorAvatar" alt="" /></div>
						<p class="meta">{{ item.creatorName }}创建 | {{ item.followers }}关注</p>
						<p class="introduction">{{ item.questionTitle.slice(0, 40) }}...</p>
						<p class="introduction">{{ item.answerAuthorName }}:{{ item.answerContent.slice(0, 40) }}...</p>
					</div>
				</div>
				<div class="card-buttom">
					<span v-for="(section, index) in item.sections" :key="index" class="section">{{ section.sectionTitle }}</span>
				</div>
			</div>
			<button class="center"><router-link to="/favorite/all" class="btn" style="color: #AAAAAA;">查看更多收藏夹 ></router-link></button>
		</div>
	</div>
</template>

<script>
export default {
	name: 'special',
	data() {
		return {
			specials: [],
			roundTables: [],
			favorites: []
		};
	},
	created() {
		this.axios.get('http://localhost:8080/api/special').then(res => {
			console.log(res);
			this.specials = res.data.data;
		});
		this.axios.get('http://localhost:8080/api/roundTable').then(res => {
			console.log(res);
			this.roundTables = res.data.data;
		});
		this.axios.get('http://localhost:8080/api/favorite').then(res => {
			console.log(res);
			this.favorites = res.data.data;
		});
	}
};
</script>

<style lang="scss" scoped>
.banner {
	width: 100%;
	margin-top: -10px;
	height: 60px;
	display: flex;
	align-items: center;
	font-size: 20px;
}
.iconfont {
	color: rgb(0, 132, 255);
	font-size: 32px;
	margin-right: 10px;
}
.r {
	margin-left: 350px;
	margin-bottom: 30px;
}
.card {
	background-color: rgb(255, 255, 255);
	height: 550px;
	margin-right: -5px;
}
.cards {
	background-color: rgb(255, 255, 255);
	height: 380px;
	margin-left: 20px;
	margin-bottom: 40px;
}
.cards-head {
	position: relative;
	height: 240px;
	// 颜色渐变
	background-image: linear-gradient(to right, rgb(0, 0, 255) 0%, rgba(0, 0, 255, 0) 100%);
}
.card_head {
	width: 100%;
}
.card-background {
	position: absolute;
	top: 0;
	right: 0;
	bottom: 0;
	width: 240px;
}
.meta {
	margin-top: -30px;
}
.card-main {
	position: relative;
	width: 320px;
	padding: 68px 24px 24px;
}
.cards-main {
	position: relative;
	width: 220px;
	padding: 68px 24px 24px;
}
.card-btn {
	position: absolute;
	right: 24px;
	bottom: 24px;
	background-color: white;
	border-radius: 5px;
}
.card-body {
	margin: 15px;
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
.introduction {
	display: flex;
	margin-top: -20px;
}
.name {
	font-size: 28px;
	font-weight: 660;
	color: white;
	margin-bottom: 30px;
}
.title {
	font-size: 28px;
	font-weight: 660;
	color: black;
	margin-bottom: 30px;
}
.col-6 {
	flex: 0 0 47%;
	// img {
	// 	width: 100%;
	// }
}
.center {
	width: 150px;
	height: 70px;
	border-radius: 47%;
}
</style>
