<template>
	<div>
		<div class="container">
			<div class="row">
				<div class="banner">
					<span>圆桌</span>	
				</div>
				<div class="col-4 card" v-for="(item, index) in roundTables" v-if="index > begin && index < end" :key="index">
					<div class="card-head">
						<img :src="item.banner" alt="" />
						<p class="name">{{ item.name }}</p>
					</div>
					<div class="meta">
						<p>该圆桌被浏览{{ item.visits_count }}次</p>
					</div>
				</div>
			</div>

			<button @click="show_all" class="flex center btn">展开全部</button>
		</div>
		<div>
			<a href="#top" style="position: fixed; bottom: 5%; right: 5%;"><i class="iconfont">&#xe604;</i></a>
		</div>
	</div>
</template>

<script>
export default {
	name: 'special',
	data() {
		return {
			roundTables: [],
			begin: 0,
			end: 9
		};
	},
	created() {
		this.axios.get('http://localhost:8080/api/roundTable/all').then(res => {
			console.log(res);
			this.roundTables = res.data.data;
		});
	},
	methods: {
		show_all() {
			this.begin = 0;
			this.end = this.roundTables.length;
		}
	}
};
</script>

<style lang="scss" scoped>
.banner {
	width: 92%;
	background-color: #ffffff;
	margin-bottom: -20px;
	margin-top: -10px;
	margin-left: 20px;
	height: 60px;
	border: 1px solid #dddddd;
	box-shadow: 2px 5px 5px #ddd;
	padding-left: 10%;
	display: flex;
	align-items: center;
	img {
		height: 60%;
	}
}
.col-4 {
	flex: 0 0 19%;
	img {
		width: 100%;
		height: 100%;
	}
}
.card {
	margin-right: 20px;
	margin-bottom: 20px;
	margin-right: 40px;
	height: 250px;
	background-color: white;
	box-shadow: 0 1px 3px 0 rgba(26, 26, 26, 0.1);
}
.card-head {
	height: 80%;
	position: relative;
}
.meta {
	height: 20%;
	background-color: white;
	margin-top: 5px;
	width: 100%;
	color: #778087;
}
.name {
	position: absolute;
	bottom: 5%;
	left: 5%;
	color: white;
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
.iconfont {
	font-size: 30px;
	color: dodgerblue;
}
</style>
