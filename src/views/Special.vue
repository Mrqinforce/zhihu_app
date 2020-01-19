<template>
	<div>
		<div class="banner">
			<i class="iconfont">&#xe71f;</i>
			<h2>全部专题</h2>
		</div>
		<div class="container">
			<div class="row" v-for="(item, index) in specials" v-if="index > begin && index < end" :key="index">
				<div class="col-4"><img :src="item.banner" alt="" /></div>
				<div class="col-8">
					<h3>{{ item.title }}</h3>
					<div class="r"><button class="btn">关注专题</button></div>
					<p class="meta" style="color: rgb(204, 204, 204);">{{ item.updated }}更新,{{ item.view_count }}次浏览</p>
					<p class="introduction">{{ item.introduction.slice(0, 40) }}...</p>
					<span v-for="(section, index) in item.sections" :key="index" class="section">{{ section.sectionTitle }}</span>
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
	name: 'special',
	data() {
		return {
			specials: [],
			begin: 0,
			end: 8
		};
	},
	created() {
		this.axios.get('http://localhost:8080/api/special/all').then(res => {
			console.log(res);
			this.specials = res.data.data;
		});
	},
	methods: {
		showAll() {
			this.begin = 0;
			this.end = this.specials.length;
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
	margin-left: 600px;
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
</style>
