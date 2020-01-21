<template>
	<div class="container">
		<div class="banner">
			<svg class="Zi Zi--LabelSpecial" fill="currentColor" viewBox="0 0 24 24" width="36" height="36" style="fill: #0084FF; margin-right: 10px;">
				<path
					d="M7.667 3.667h11.466a1.2 1.2 0 0 1 1.2 1.2v13.066a2.4 2.4 0 0 1-2.4 2.4H6.467V4.867a1.2 1.2 0 0 1 1.2-1.2zM4.2 9.619h1.689v10.714H5.4a2.4 2.4 0 0 1-2.4-2.4V10.82a1.2 1.2 0 0 1 1.2-1.2zm5.178-2.38a.6.6 0 0 0-.6.6v.585a.6.6 0 0 0 .6.6h8.044a.6.6 0 0 0 .6-.6v-.586a.6.6 0 0 0-.6-.6H9.378zm0 3.57a.6.6 0 0 0-.6.6v.586a.6.6 0 0 0 .6.6h8.044a.6.6 0 0 0 .6-.6v-.585a.6.6 0 0 0-.6-.6H9.378zm0 3.572a.6.6 0 0 0-.6.6v.586a.6.6 0 0 0 .6.6h4.578a.6.6 0 0 0 .6-.6v-.586a.6.6 0 0 0-.6-.6H9.378z"
					fill-rule="evenodd"
				></path>
			</svg>
			<h3>最新专题</h3>
		</div>
		<div class="row">
			<div class="col-6 card" v-for="(item, index) in specials" :key="index">
				<div><img :src="item.banner" alt="" /></div>
				<div class="card-body">
					<h3>{{ item.title }}</h3>
					<div class="attention"><button class="btn">关注专题</button></div>
					<p class="meta">{{ item.updated }}更新,{{ item.viewCount }}次浏览</p>
					<p class="introduction">{{ item.introduction.slice(0, 40) }}...</p>
				</div>
				<span v-for="(section, index) in item.sections" :key="index" class="section">{{ section.sectionTitle }}</span>
			</div>
			<button class="center"><router-link to="/special/all" class="btn" style="color: #AAAAAA;">查看更多专题 ></router-link></button>
		</div>
		<div class="row">
			<div class="banner">
				<svg class="Zi Zi--LabelRoundtable" viewBox="0 0 24 24" width="36" height="36" style="fill: #0084FF;margin-right: 10px;">
					<path
						d="M12 21.333a9.333 9.333 0 1 1 0-18.666 9.333 9.333 0 0 1 0 18.666zm-.66-11.287c.332.385.609.77.775 1.21.055-.054.665-.99.72-1.706.055-.385.126-1.616-.443-2.367-.443-.496-1.219-.77-1.884-.55a1.788 1.788 0 0 0-1.33 2.036c.887.276 1.607.771 2.161 1.377zm-1.33 1.541c.443-.055.941-.11 1.44 0 0-.055-.484-.936-1.108-1.486-.665-.496-1.33-.973-2.216-.771-.72.11-1.723.77-1.55 2.092.11.606.553 1.101 1.162 1.321.61-.605 1.44-1.046 2.272-1.156zm2.714.165c.056 0 1.164.055 1.828-.165.72-.275 1.412-.68 1.773-1.541.11-.276.23-1.248-.443-1.872-.72-.716-1.717-.716-2.438-.165.222.825.063 1.966-.11 2.532-.103.348-.333.88-.61 1.211zm-1.44.55c-.056 0-1.33.056-1.828.221-.72.275-1.447.668-1.773 1.541-.11.276-.21 1.26.443 1.872.665.661 1.718.661 2.438.11-.295-.811-.166-1.761.055-2.477.166-.495.388-.936.665-1.266zm5.041-.99c-.665.605-1.44.99-2.327 1.211-.443.055-.941.11-1.44 0 0 .055.554.991 1.108 1.431.665.496 1.385.771 2.216.771.72-.11 1.678-.692 1.551-2.092-.055-.605-.554-1.101-1.108-1.321zm-3.656 2.642a3.475 3.475 0 0 1-.776-1.156c-.055.055-.665.991-.72 1.707-.055.385-.101 1.506.499 2.312.443.496 1.218.77 1.883.55.887-.275 1.496-1.1 1.33-2.036a5.38 5.38 0 0 1-2.216-1.377z"
						fill-rule="evenodd"
					></path>
				</svg>
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
			<button class="center"><router-link to="/roundTable/all" class="btn" style="color: #AAAAAA;">查看更多专题 ></router-link></button>
		</div>
		<div class="row">
			<div class="banner">
				<svg class="Zi Zi--Star" fill="currentColor" viewBox="0 0 24 24" width="36" height="36" style="color: #0084FF; margin-right: 10px;">
					<path
						d="M5.515 19.64l.918-5.355-3.89-3.792c-.926-.902-.639-1.784.64-1.97L8.56 7.74l2.404-4.871c.572-1.16 1.5-1.16 2.072 0L15.44 7.74l5.377.782c1.28.186 1.566 1.068.64 1.97l-3.89 3.793.918 5.354c.219 1.274-.532 1.82-1.676 1.218L12 18.33l-4.808 2.528c-1.145.602-1.896.056-1.677-1.218z"
						fill-rule="evenodd"
					></path>
				</svg>
				<h3>热门收藏夹</h3>
			</div>
			<div class="col-6 cards" v-for="(item, index) in favorites" :key="index">
				<div class="favorite">
									<p class="favorite_title">{{ item.title }}</p>
									<button class="favorite_attention"><h4>关注收藏夹</h4></button>
									<img :src="item.creatorAvatar" />
									<p class="favorite_name">{{ item.creatorName }}</p>
									<p class="favorite_create">创建 | {{ item.followers }}人关注</p>								
								</div>
								
								<div class="popular">
									<p class="popular_title">{{item.questionTitle}}</p>
									<p class="popular_content">{{item.answerAuthorName}}: {{item.answerContent}}</p>			
									<span class="popular_reply">回答</span>
									<span class="popular_agree">{{item.voteupCount}}赞同 {{item.commentCount}}评论</span>
								</div>
								<div class="bottom">
									<h4 class="content">已收藏{{ item.totalCount }}条内容 ></h4>
								</div>
							</div>
						</div>
			<button class="center_third"><router-link to="/favorite/all" class="btn" style="color: #AAAAAA;">查看更多收藏夹 ></router-link></button>
			<!-- <svg class="Zi Zi--Feedback" title="建议反馈" fill="currentColor" viewBox="0 0 24 24" width="24" height="24">
				<path
					d="M19.99 6.99L18 5s-1-1-2-1H8C7 4 6 5 6 5L4 7S3 8 3 9v9s0 2 2.002 2H19c2 0 2-2 2-2V9c0-1-1.01-2.01-1.01-2.01zM16.5 5.5L19 8H5l2.5-2.5h9zm-2 5.5s.5 0 .5.5-.5.5-.5.5h-5s-.5 0-.5-.5.5-.5.5-.5h5z"
					style="position: fixed; bottom: 20%; right: 10%;"
				></path>
			</svg> -->
		</div>
		
	</div>
</template>

<script>
export default {
	name: 'explore',
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
.attention {
	margin-left: 350px;
	margin-bottom: 30px;
}

.card {
	background-color: rgb(255, 255, 255);
	height: 500px;
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
.metatwo {
	margin-top: 10px;
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
.center_third {
	margin-left: 500px;
	width: 150px;
	height: 70px;
	border-radius: 47%;
}
.favorite {
		position: relative;
		height: 30%;
		img {
			position: absolute;
			top: 65px;
			left: 20px;
		}
		.favorite_title {
			position: absolute;
			top: 20px;
			left: 20px;
			display: block;
			height: 28px;
			line-height: 28px;
			font-size: 20px;
			font-weight: 600;
		}
		.favorite_attention {
			position: absolute;
			top: 20px;
			right: 30px;
			border: none;
			color: #0084ff;
			background-color: rgba(0, 132, 255, 0.08);
			height: 30px;
			border-radius: 5px;
			font-size: 14px;
		}
		.favorite_create {
			position: absolute;
			top: 60px;
			left: 120px;
			font-size: 14px;
			color: #999;
		}
		.favorite_name {
			position: absolute;
			top: 60px;
			left: 63px;
			color: #444;
			font-weight: 500;
		}
	}
	.popular {
			position: relative;
			height: 50%;	
			border-top: 1px solid #ebebeb;
			width: 90%;		
			left: 20px;
			.popular_title{
				position: absolute;
				font-weight: 600;
				line-height: 21px;
				top: 20px;
			}
			.popular_content{
				position: absolute;
				top: 55px;
				height: 21px;
				line-height: 21px;
				color: #444;
			}
			.popular_reply{
				position: absolute;
				top: 180px;
				left: 5px;
				background-color: #f6f6f6;
				color: #999;
				font-size: 12px;
			}
			.popular_agree{
				position: absolute;
				top: 180px;
				left: 45px;
				height: 17px;
				line-height: 17px;
				font-size: 12px;
				color: #999;
			}
		}
		.bottom {
			position: relative;
			height: 20%;
			font-size: 14px;
			color: #8590a6;		
			.content{
				position: absolute;
				left: 22px;
				top: 20px;
			}
		}
	
</style>
