<template>
	<div class="login-bar tx-center">
		<router-link to="/"><img src="https://pic4.zhimg.com/80/v2-a47051e92cf74930bedd7469978e6c08_hd.png" class="logo" /></router-link>
		<div class="login-box">
			<div class="tab">
				<span class="tab-item" :class="{ active: isActive }" @click="changeTab">免密码登录</span>
				<span class="tab-item" :class="{ active: !isActive }" @click="changeTab">密码登录</span>
				<svg width="52" height="52" xmlns:xlink="http://www.w3.org/1999/xlink" fill="currentColor" class="pull-right">
					<defs><path id="id-3938311804-a" d="M0 0h48a4 4 0 0 1 4 4v48L0 0z"></path></defs>
					<g fill="none" fill-rule="evenodd">
						<mask id="id-3938311804-b" fill="#fff"><use xlink:href="#id-3938311804-a"></use></mask>
						<use fill="#0084FF" xlink:href="#id-3938311804-a"></use>
						<image
							width="52"
							height="52"
							mask="url(#id-3938311804-b)"
							xlink:href="data:image/png;base64,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"
						></image>
					</g>
				</svg>
			</div>

			<div class="tab-box" v-if="show && selected === 0">
				<div class="sign-account">
					<div class="sign-country">
						<div class="Popover">
							<button
								role="combobox"
								aria-expanded="false"
								id="Popover18-toggle"
								aria-haspopup="true"
								aria-owns="Popover18-content"
								type="button"
								class="InputButton"
							>
								中国 +86
								<svg class="Zi--Select" fill="currentColor" viewBox="0 0 24 24" width="24" height="24">
									<path
										d="M12 16.183l2.716-2.966a.757.757 0 0 1 1.064.001.738.738 0 0 1 0 1.052l-3.247 3.512a.758.758 0 0 1-1.064 0L8.22 14.27a.738.738 0 0 1 0-1.052.758.758 0 0 1 1.063 0L12 16.183zm0-9.365L9.284 9.782a.758.758 0 0 1-1.064 0 .738.738 0 0 1 0-1.052l3.248-3.512a.758.758 0 0 1 1.065 0L15.78 8.73a.738.738 0 0 1 0 1.052.757.757 0 0 1-1.063.001L12 6.818z"
										fill-rule="evenodd"
									></path>
								</svg>
							</button>
						</div>
					</div>
					<span class="SignFlow-accountSeperator">&nbsp;</span>
					<div class="sign-mbnumber">
						<label class="Input-wrapper"><input name="username" type="tel" class="Input" placeholder="手机号" value="" /></label>
					</div>
				</div>
				<div class="sign-password">
					<div class="Input-password">
						<label class="Input-wrapper"><input name="username" type="tel" class="Input" placeholder="输入六位短信验证码" value="" /></label>
					</div>
					<button type="button" class="SignFlow-smsInputButton">获取短信验证码</button>
				</div>
				<div class="Login-option">
					<button></button>
					<button type="button">接收语音验证码</button>
				</div>
				<button type="submit" class=" SignFlow-submitButton ">注册/登录</button>
				<div class="SignContainer-tip">
					<div>
						<div class="zzz">未注册手机验证后自动登录</div>
						<div>
							注册即代表同意
							<a href="https://www.zhihu.com/terms">《知乎协议》</a>
							<a href="https://www.zhihu.com/term/privacy">《隐私保护指引》</a>
						</div>
					</div>
					<a href="https://www.zhihu.com/org/signup" class="aaa">注册机构号</a>
				</div>
			</div>

			<div class="tab-box" style="height: 31 0px;" v-if="show && selected === 1">
				<div class="sign-mbnumber">
					<label class="Input-wrapper"><input name="username" type="tel" class="Input" placeholder="手机号或邮箱" value="" /></label>
				</div>
				<div class="Input-password">
					<label class="Input-wrapper"><input name="username" type="tel" class="Input" placeholder="密码" value="" /></label>
				</div>
				<div class="Login-option">
					<button type="button" class="aaa">海外手机号登录</button>
					<button type="button">忘记密码？</button>
				</div>
				<button type="submit" class=" SignFlow-submitButton  ">注册/登录</button>
				<div class="SignContainer-tip">
					<div>
						<div class="zzz">未注册手机验证后自动登录</div>
						<div>
							注册即代表同意
							<a href="https://www.zhihu.com/terms">《知乎协议》</a>
							<a href="https://www.zhihu.com/term/privacy">《隐私保护指引》</a>
						</div>
					</div>
					<a href="https://www.zhihu.com/org/signup" class="aaa">注册机构号</a>
				</div>
			</div>
		</div>
		<div class="login-social">
			<span>社交帐号登录</span>
			<span class="login-btngroup">
				<div class="login-btn">
					<svg
						viewBox="0 0 20 19"
						class="Icon Login-socialIcon Icon--wechat"
						width="18"
						height="18"
						aria-hidden="true"
						style="fill: rgb(96, 200, 77); height: 18px; width: 18px;"
					>
						<title></title>
						<g>
							<path
								fill-rule="evenodd"
								d="M.224 18.667s4.24-1.825 4.788-2.056C13.03 20.14 20 14.715 20 8.9 20 3.984 15.523 0 10 0S0 3.984 0 8.898c0 1.86.64 3.585 1.737 5.013-.274.834-1.513 4.757-1.513 4.757zM6.167 8.96c.69 0 1.25-.57 1.25-1.27 0-.703-.56-1.272-1.25-1.272s-1.25.57-1.25 1.27c0 .703.56 1.272 1.25 1.272zm7.583 0c.69 0 1.25-.57 1.25-1.27 0-.703-.56-1.272-1.25-1.272s-1.25.57-1.25 1.27c0 .703.56 1.272 1.25 1.272z"
							></path>
						</g>
					</svg>
					微信
				</div>
				<div class="login-btn">
					<svg
						width="18"
						height="18"
						viewBox="0 0 18 20"
						xmlns="http://www.w3.org/2000/svg"
						class="Icon Login-socialIcon Icon--qq"
						aria-hidden="true"
						style="fill: rgb(80, 200, 253); height: 18px; width: 18px;"
					>
						<title></title>
						<g>
							<title>QQ</title>
							<path
								d="M9.003 0c-2.265 0-6.29 1.364-6.29 7.325V8.52S.55 12.96.55 15.474c0 .665.17 1.025.28 1.025.115 0 .903-.485 1.75-2.073 0 0-.18 2.197 1.903 3.967 0 0-1.77.495-1.77 1.182 0 .686 4.078.43 6.29 0 2.24.425 6.287.687 6.287 0 0-.688-1.768-1.182-1.768-1.182 2.085-1.77 1.905-3.967 1.905-3.967.845 1.588 1.634 2.072 1.746 2.072.11 0 .283-.36.283-1.026 0-2.514-2.166-6.954-2.166-6.954V7.325C15.29 1.365 11.268 0 9.003 0z"
								fill-rule="evenodd"
							></path>
						</g>
					</svg>
					QQ
				</div>
				<div class="login-btn">
					<svg
						viewBox="0 0 22 18"
						class="Icon Login-socialIcon Icon--weibo"
						width="18"
						height="18"
						aria-hidden="true"
						style="fill: rgb(251, 102, 34); height: 18px; width: 18px;"
					>
						<title></title>
						<g>
							<g fill-rule="evenodd">
								<path
									d="M14.518.06s-.87.644.03 1.71c0 0 6.287-1.19 5.69 6.33 0 0 1.05 1.13 1.674-.31 0 .002 1.44-8.584-7.394-7.73zM4.883 13.17s.038 2.584 3.326 2.584c3.657 0 3.683-2.98 3.683-2.98S12.1 9.67 8.687 9.61c-3.863-.07-3.804 3.56-3.804 3.56zM7.41 14.21c-.668 0-1.214-.447-1.214-.998 0-.55.543-.998 1.215-.998.67 0 1.213.447 1.213.998 0 .55-.54.998-1.212.998z"
								></path>
								<path
									d="M4.317 4.52C-2.603 10.353.873 14.85.873 14.85c.57 1.01 3.382 3.1 8.596 3.1 5.21 0 9.314-3.628 9.314-6.44 0-2.813-2.918-2.714-2.918-2.714 1.04-1.554.19-2.65.19-2.65-1.684-2.118-5.404-.16-5.407-.158.772-1.717.11-2.797.11-2.797C8.932.66 4.317 4.52 4.317 4.52zm10.448 7.79s-.467 4.16-6.447 4.16c-5.745 0-5.82-3.322-5.842-3.712 0 0-.073-4.423 6.58-4.654 5.94-.204 5.71 4.207 5.71 4.207zM18.65 7.045s1.018-4.37-3.864-3.818c0 0-.628.58.09 1.346 0 0 2.602-.58 2.397 2.598 0 0 .715.885 1.376-.125z"
								></path>
							</g>
						</g>
					</svg>
					微博
				</div>
			</span>
		</div>
		<button type="button" class="SignFlowHomepage-downloadBtn">
			<div>
				<svg width="20" height="20" fill="currentColor">
					<g fill="none" fill-rule="evenodd">
						<path
							fill="#0084FF"
							d="M15.234 0C18.125 0 20 1.875 20 4.766v10.468C20 18.125 18.125 20 15.234 20H4.766C1.875 20 0 18.125 0 15.234V4.766C0 1.875 1.875 0 4.766 0h10.468z"
						></path>
						<path d="M0 0h20v20H0z"></path>
						<path
							fill="#FFF"
							d="M10.313 10.352c0-.012-.004-1.036-.328-1.055h-2.26a48.42 48.42 0 0 0 .095-3.164h2.21c0-.003.084-.982-.37-.977H5.837c.15-.563.34-1.15.566-1.758 0 0-1.039 0-1.393.937-.146.386-.57 1.87-1.325 3.388.254-.028 1.095-.05 1.59-.963.091-.255.109-.289.222-.627h1.246c0 .452-.051 2.897-.072 3.164H4.414c-.507.019-.672 1.043-.672 1.055h2.832c-.19 2.15-1.209 3.972-3.058 5.413.884.253 1.766-.04 2.202-.43 0 0 .992-.906 1.536-3.004l2.33 2.817s.342-1.166-.053-1.734c-.328-.387-1.212-1.434-1.589-1.814l-.631.504a7.686 7.686 0 0 0 .34-1.752h2.662zM10.898 5v9.441h1.015l.334 1.145 1.82-1.144h2.144V5h-5.313zm4.258 8.398h-1.214l-1.212.782-.22-.782h-.518V6.016h3.164v7.382z"
						></path>
					</g>
				</svg>
				下载知乎 App
			</div>
		</button>
		<footer class="SignFlowHomepage-footer">
			<div class="ZhihuLinks ">
				<a target="_blank" rel="noopener noreferrer" href="https://zhuanlan.zhihu.com" class="bbb">知乎专栏</a>
				<a target="_blank" rel="noopener noreferrer" href="/roundtable" class="bbb">圆桌</a>
				<a target="_blank" rel="noopener noreferrer" href="/explore" class="bbb">发现</a>
				<a target="_blank" rel="noopener noreferrer" href="/app" class="bbb">移动应用</a>
				<a target="_blank" rel="noopener noreferrer" href="/contact" class="bbb">联系我们</a>
				<a target="_blank" rel="noopener noreferrer" href="https://app.mokahr.com/apply/zhihu" class="bbb">来知乎工作</a>
				<a target="_blank" rel="noopener noreferrer" href="/org/signup" class="bbb">注册机构号</a>
			</div>
			<div class="ZhihuRights">
				<span>© 2020 知乎</span>
				<a target="_blank" rel="noopener noreferrer" href="https://tsm.miit.gov.cn/dxxzsp/" class="bbb">京 ICP 证 110745 号</a>
				<a target="_blank" rel="noopener noreferrer" href="http://www.beian.miit.gov.cn" class="bbb">京 ICP 备 13052560 号 - 1</a>
				<a target="_blank" rel="noopener noreferrer" href="http://www.beian.gov.cn/portal/registerSystemInfo?recordcode=11010802020088" class="bbb">
					<img src="https://pic3.zhimg.com/80/v2-d0289dc0a46fc5b15b3363ffa78cf6c7.png" />
					京公网安备 11010802010035 号
				</a>
				<a href="https://zhstatic.zhihu.com/assets/zhihu/publish-license.jpg" target="_blank" rel="noopener noreferrer" class="bbb">出版物经营许可证</a>
			</div>
			<div class="ZhihuReports">
				<a target="_blank" rel="noopener noreferrer" href="https://zhuanlan.zhihu.com/p/51068775" class="bbb">侵权举报</a>
				<a target="_blank" rel="noopener noreferrer" href="http://www.12377.cn" class="bbb">网上有害信息举报专区</a>
				<a target="_blank" rel="noopener noreferrer" href="/jubao" class="bbb">儿童色情信息举报专区</a>
				<span>违法和不良信息举报：010-82716601</span>
			</div>
		</footer>
	</div>
</template>

<script>
export default {
	data() {
		return {
			isActive: true,
			show: true,
			selected: 0
		};
	},
	methods: {
		changeTab: function() {
			this.isActive = !this.isActive;
			this.selected = this.selected == 0 ? 1 : 0;
		}
	}
};
</script>
<style lang="scss" scoped>
.login-bar {
	background-image: url(https://static.zhihu.com/heifetz/assets/sign_bg.db29b0fb.png);
	background-repeat: no-repeat;
	background-color: #b8e5f8;
	background-size: cover;
	width: 100%;
	height: 100%;
	overflow: auto;
	.logo {
		width: 128px;
		height: 81px;
		margin-bottom: 24px;
		margin-top: 30px;
	}
}
.login-box {
	background: #fff;
	border-radius: 2px;
	box-shadow: 0 1px 3px rgba(26, 26, 26, 0.1);
	box-sizing: border-box;
	width: 400px;
	margin: 0 auto;
	text-align: center;
	position: relative;
	border-radius: 4px;
	box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1);
	padding-left: 20px;
}
/* 顶部div */
.tab {
	text-align: left;
}
.tab-item {
	font-family: -apple-system, BlinkMacSystemFont, Helvetica Neue, PingFang SC, Microsoft YaHei, Source Han Sans SC, Noto Sans CJK SC, WenQuanYi Micro Hei, sans-serif;
	-webkit-tap-highlight-color: rgba(26, 26, 26, 0);
	-webkit-box-direction: normal;
	text-align: left;
	display: inline-block;
	font-size: 16px;
	line-height: 60px;
	height: 60px;
	margin-right: 24px;
	cursor: pointer;
	position: relative;
	color: #1a1a1a;
	font-weight: 600;
}
.active {
	color: black;
	font-weight: 700;
	border-bottom: 3px solid dodgerblue;
}
/* 中间div */
.tab-box {
	text-align: center;
	overflow: hidden;
	padding: 0 24px 84px;
}
.sign-account {
	text-align: center;
	margin-top: 24px;
	border-bottom: 1px solid #ebebeb;
	display: flex;
	align-items: center;
}
.sign-country {
	text-align: center;
	display: inline-block;
	min-width: 72px;
}
.Popover {
	text-align: center;
	position: relative;
	display: inline-block;
}
.SignFlow-accountSeperator {
	text-align: center;
	width: 1px;
	height: 22px;
	margin: 0 12px;
	background: #ebebeb;
}
.InputButton {
	margin: 0;
	font-size: 14px;
	color: #8590a6;
	cursor: pointer;
	height: auto;
	line-height: inherit;
	background: #fff;
	border-radius: 3px;
	box-sizing: border-box;
	transition: background 0.2s, border 0.2s;
	display: flex;
	align-items: center;
	text-align: left;
	padding: 0;
	border: 1px solid transparent;
}
.Zi--Select {
	font-size: 14px;
	color: #8590a6;
	cursor: pointer;
	line-height: inherit;
	text-align: left;
	fill: currentcolor;
	width: 24;
	height: 24;
	margin-left: 8px;
}
.sign-mbnumber {
	text-align: center;
	position: relative;
	flex: 1 1;
	.Input-wrapper {
		text-align: center;
		position: relative;
		display: flex;
		align-items: center;
		font-size: 14px;
		background: #fff;
		box-sizing: border-box;
		transition: background 0.2s, border 0.2s;
		width: 100%;
		height: 48px;
		padding: 0;
		color: #8590a6;
		border: none;
		border-bottom: 1px solid #ebebeb;
		border-radius: 0;
	}
	.Input {
		flex: 1 1;
		padding: 0;
		overflow: hidden;
		font-family: inherit;
		font-size: inherit;
		font-weight: inherit;
		background: transparent;
		border: none;
		resize: none;
		color: #1a1a1a;
		line-height: 24px;
		height: 48px;
	}
}
.sign-password {
	text-align: center;
	overflow: hidden;
	position: relative;
	margin-top: 12px;
}
.Input-password {
	text-align: center;
	position: relative;
	width: auto;
	.Input-wrapper {
		text-align: center;
		position: relative;
		display: flex;
		align-items: center;
		font-size: 14px;
		background: #fff;
		box-sizing: border-box;
		transition: background 0.2s, border 0.2s;
		width: 100%;
		height: 48px;
		padding: 0;
		color: #8590a6;
		border: none;
		border-bottom: 1px solid #ebebeb;
		border-radius: 0;
	}
	.Input {
		flex: 1 1;
		padding: 0;
		overflow: hidden;
		font-family: inherit;
		font-size: inherit;
		font-weight: inherit;
		background: transparent;
		border: none;
		resize: none;
		color: #1a1a1a;
		line-height: 24px;
		height: 48px;
	}
}
.SignFlow-smsInputButton {
	margin: 0;
	display: inline-block;
	font-size: 14px;
	text-align: center;
	cursor: pointer;
	background: none;
	height: auto;
	line-height: inherit;
	background-color: transparent;
	border: none;
	border-radius: 0;
	position: absolute;
	top: 24px;
	right: 0;
	padding: 4px 0;
	color: #175199;
	transform: translateY(-50%);
}
.Login-option {
	text-align: center;
	margin-top: 12px;
	height: 20px;
	display: flex;
	justify-content: space-between;
	background: #fff;
	button {
		margin: 0;
		display: inline-block;
		font-size: 14px;
		color: #8590a6;
		text-align: center;
		cursor: pointer;
		background: none;
		height: auto;
		padding: 0;
		line-height: inherit;
		background-color: transparent;
		border: none;
		border-radius: 0;
		float: right;
	}
	.aaa {
		color: darkblue;
	}
}
.SignFlow-submitButton {
	margin: 0;
	display: inline-block;
	padding: 0 16px;
	font-size: 14px;
	line-height: 32px;
	text-align: center;
	cursor: pointer;
	background: none;
	border: 1px solid;
	border-radius: 3px;
	border-color: #0084ff;
	width: 100%;
	margin-top: 30px;
	margin-left: -20px;
	height: 36px;
	color: #fff;
	background-color: #0084ff;
}
.SignContainer-tip {
	text-align: center;
	position: absolute;
	bottom: 0;
	left: 0;
	right: 0;
	display: flex;
	align-items: center;
	justify-content: space-between;
	padding: 12px 24px;
	color: grey;
	font-size: 13px;
	background-color: #f6f6f6;
}
.login-social {
	margin: 0 auto;
	text-align: center;
	margin-bottom: 10px;
	background: #fff;
	box-sizing: border-box;
	display: flex;
	justify-content: space-between;
	color: #8590a6;
	margin-top: 24px;
	width: 400px;
	border-radius: 4px;
	box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1);
	height: 60px;
	line-height: 60px;
	padding: 0 24px;
	overflow: visible;
	.login-btngroup {
		color: #8590a6;
		line-height: 60px;
		display: flex;
		margin-left: 2px;
		transition: opacity 0.3s ease;
	}
	.login-btn {
		color: #8590a6;
		line-height: 60px;
		display: inline-flex;
		-webkit-box-align: center;
		align-items: center;
		cursor: pointer;
		margin-left: 20px;
	}
	svg {
		margin-right: 5px;
	}
}
.SignFlowHomepage-downloadBtn {
	margin: 0;
	display: inline-block;
	padding: 0 16px;
	font-size: 14px;
	line-height: 32px;
	text-align: center;
	cursor: pointer;
	border-radius: 3px;
	background: #fff;
	border: none;
	color: #0084ff;
	width: 400px;
	height: 42px;
	margin-top: 14px;
}
.SignFlowHomepage-footer {
	font-size: 12px;
	line-height: 21px;
	text-align: center;
	color: #fff;
	text-shadow: 0 1px 2px #999;
	padding-bottom: 20px;
}
.zzz {
	margin-left: -120px;
}
a {
	color: gray;
}
.aaa {
	color: darkblue;
}
.bbb {
	color: white;
}
</style>
