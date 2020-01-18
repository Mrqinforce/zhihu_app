<template>
	<div>
		<div class="nav gutter">
			<div class="nav-bar">
				<ul>
					<li><router-link to="/home">首页</router-link></li>
					<li><router-link to="/explore">发现</router-link></li>
					<li><router-link to="/question/waiting">等你来答</router-link></li>
					<li class="abs-center-right"><router-link to="/login">登录</router-link></li>
				</ul>
			</div>
		</div>
		<!--二级路由入口 -->
		<router-view />
	</div>
</template>

<script>
export default {
	name: 'nav',
	data() {
		return {};
	},
	created() {}
};
</script>
<style lang="scss" scoped>
.gutter {
	position: relative;
	margin-bottom: 10px;
}
ul {
	list-style-type: none;
	margin: 0;
	padding: 0;
	overflow: hidden;
	background-color: #ffffff;
	position: fixed;
	top: 0;
	width: 100%;
}
li {
	font-size: larger;
	margin-top: 10px;
	margin-left: 100px;
	float: left;
}

li a {
	display: block;
	color: grey;
	text-align: center;
	padding: 14px 16px;
	text-decoration: none;
}
.router-link-active {
	color: black;
	border-bottom: 2px solid #ffffff;
}
.nav-bar {
	position: sticky;
	top: 10px;
	border-bottom: 5px solid #DDDDDD;
}
</style>
