<template>
	<div>
		<div class="container">
			<div class="row" v-for="(item, index) in specials" :key="index">
				<div class="col-4"><img :src="item.banner" alt="" /></div>
				<div class="col-8">
					<h3>{{ item.title }}</h3>
					<p class="meta" style="color: rgb(204, 204, 204);;">{{ item.updated }}更新,{{ item.view_count }}次浏览</p>
					<p class="introduction">{{ item.introduction.slice(0, 40) }}...</p>
					<span v-for="(section, index) in item.sections" :key="index" class="section">{{ section.sectionTitle }}</span>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: 'special',
	data() {
		return {
			specials: []
		};
	},
	created() {
		this.axios.get('http://localhost:8080/api/special').then(res => {
			console.log(res);
			this.specials = res.data.data;
		});
	}
};
</script>

<style lang="scss" scoped>
.banner {
	width: 100%;
	background-color: #ffffff;
	margin-bottom: 10px;
	margin-top: -10px;
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

.container {
	background-color: #ffffff;
	.row {
		display: flex;
		margin-bottom: 10px;
		border: 1px solid #d6d6d6;
		border-radius: 4px;
		width: 100%;
		height: 180px;
		padding: 14px;
		box-shadow: 0 1px 3px 0 rgba(26, 26, 26, 0.1);
		.col-4 {
			flex: 0 0 33%;
			height: 100%;
			img {
				width: 80%;
				height: 100%;
				border-radius: 5px;
			}
		}
	}
}
</style>
