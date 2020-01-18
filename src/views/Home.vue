<template>
	<div>
		<div class="container">
		<div class="banner">
			<ul>
				<li>
					<router-link to="/home/recommoned" class="router"><p class="font">推荐</p></router-link>
				</li>
				<li>
					<router-link to="/home/follow" class="router"><p class="font">关注</p></router-link>
				</li>
				<li>
					<router-link to="/home/hot" class="router"><p class="font">热榜</p></router-link>
				</li>
			</ul>
		</div>
		
		
			</div>
			<router-view />
	</div>
</template>

<script>
// export default {
// 	name: 'recommoned',
// 	data() {
// 		return {
// 			recommoned: []
// 		};
// 	},
// 	created() {
// 		this.axios.get('http://localhost:8080/api/special').then(res => {
// 			console.log(res);
// 			this.recommoned = res.data.data;
// 		});
// 	}
// };
</script>
<style lang="scss" scoped>
ul {
	list-style-type: none;
}
li {
	font-size: larger;
	margin-top: 10px;
	margin-left: 50px;
	float: left;
}
.banner {
	margin-bottom: 4px;
	margin-top: 10px;
	height: 100px;
	background-color: #ffffff;
	border: 1px solid #ffffff;
	box-shadow: 2px 5px 5px #ddd;
	display: flex;
	align-items: center;
}
.font {
	color: #000000;
	font-size: 20px;
}
</style>
