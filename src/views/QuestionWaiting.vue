<template>
	<div>
		<div class="container">
			<div class="row">
				<div class="col-8">
					<!-- 顶部tab导航 -->
					<ul class="tab-title border-bottom">
						<li v-for="(title, index) in tabTitle" @click="change(index)" :class="{ active: cur == index }" :key="index">
							<div v-if="title === '人气问题'" class="tab-info">
								<svg class="Zi Zi--Fire QuestionType-icon" fill="currentColor" viewBox="0 0 24 24" width="18" height="18">
									<path
										d="M14.553 20.78c.862-.651 1.39-1.792 1.583-3.421.298-2.511-.656-4.904-2.863-7.179.209 2.291.209 3.73 0 4.314-.41 1.143-1.123 1.983-1.91 2.03-1.35.079-2.305-.512-2.863-1.774-.676 1.25-.782 2.556-.318 3.915.31.906.94 1.684 1.89 2.333C7.144 20.131 5 17.336 5 14.022c0-2.144.898-4.072 2.325-5.4.062 2.072.682 3.598 2.13 4.822-.67-1.112-.734-2.11-.734-3.517 0-3.253 2.067-6.007 4.913-6.927a7.35 7.35 0 0 0 2.157 4.918C17.722 9.214 19 11.463 19 14.022c0 3.073-1.844 5.7-4.447 6.758z"
										fill-rule="evenodd"
									></path>
								</svg>
								{{ title }}
							</div>
							<div v-if="title === '潜力好问'" class="tab-info">
								<svg class="Zi Zi--Seed QuestionType-icon" fill="currentColor" viewBox="0 0 24 24" width="18" height="18">
									<path
										d="M10.558 9.842c.745 1.423 1.148 2.996 1.283 4.574a14.663 14.663 0 0 1 .052 1.125 16.067 16.067 0 0 1-.491 4.078l-.028.104a.232.232 0 0 1-.295.155l-.94-.302a.221.221 0 0 1-.148-.277l.018-.055a13.683 13.683 0 0 0 .234-.852 14.827 14.827 0 0 0 .4-2.89.225.225 0 0 0-.176-.223 11.89 11.89 0 0 1-1.383-.42 11.508 11.508 0 0 1-1.806-.86 10.681 10.681 0 0 1-2.98-2.581A10.213 10.213 0 0 1 3.23 9.784 10.388 10.388 0 0 1 2.49 8a10.772 10.772 0 0 1-.406-1.87 9.95 9.95 0 0 1-.062-1.922.229.229 0 0 1 .29-.2c1.707.321 3.366.97 4.806 1.964a10.75 10.75 0 0 1 3.44 3.87zm12.04-2.252l.01.002c.117.03.19.147.165.266a8.966 8.966 0 0 1-1.274 3.592 8.552 8.552 0 0 1-1.204 1.521 8.724 8.724 0 0 1-1.53 1.212 8.872 8.872 0 0 1-3.674 1.233c-.235.027-.47.045-.705.056a.225.225 0 0 0-.207.256c.034.262.084.522.148.778a.223.223 0 0 1-.162.269l-.859.218a.223.223 0 0 1-.273-.177 8.418 8.418 0 0 1-.102-2.458c.05-.469.14-.932.27-1.384a7.868 7.868 0 0 1 2.234-3.63c.062-.057.123-.114.189-.167l.193-.161c.065-.053.133-.103.2-.153.13-.104.273-.194.41-.289.144-.086.284-.178.432-.255.144-.084.296-.155.445-.229.152-.067.303-.136.46-.194.309-.118.625-.22.946-.296a8.357 8.357 0 0 1 1.947-.23 8.143 8.143 0 0 1 1.941.22z"
									></path>
								</svg>
								{{ title }}
							</div>
							<div v-if="title === '新问题'" class="tab-info">
								<svg class="Zi Zi--New QuestionType-icon" fill="currentColor" viewBox="0 0 24 24" width="18" height="18">
									<path
										d="M3.111 2.667H20.89c.614 0 1.111.497 1.111 1.11v14.091c0 .45-.272.857-.689 1.028l-8.73 3.585c-.462.19-.98.187-1.441-.007L2.679 18.9A1.111 1.111 0 0 1 2 17.876V3.778c0-.614.497-1.111 1.111-1.111zm2.503 10.75v-2.753h.064l2.024 2.753h.977V8.573H7.51v2.725h-.064L5.429 8.573h-.983v4.844h1.168zm7.526-.99h-2.088v-.99h1.964v-.907h-1.964v-.967h2.088v-.99H9.82v4.844h3.32v-.99zm3.992-1.978h.06l.809 2.968h1.155l1.265-4.844h-1.269l-.634 3.212h-.06l-.803-3.212h-.987l-.775 3.212h-.06l-.645-3.212h-1.28l1.266 4.844h1.162l.796-2.968z"
										fill-rule="evenodd"
									></path>
								</svg>
								{{ title }}
							</div>
							<div v-if="title === '人人答'" class="tab-info">
								<svg class="Zi Zi--Creator QuestionType-icon" fill="currentColor" viewBox="0 0 24 24" width="18" height="18">
									<path
										d="M15.075 15.388l-3.024 3.024a4.041 4.041 0 0 0-1.014 1.697l-.26.868C7.844 20.986 4.91 21 2 21c.026-3.325 0-3.304.59-3.956 1.237-1.368 6.251-.68 6.44-2.976.043-.518-.36-1.06-.725-1.69C6.285 8.87 5.512 2 11.5 2c5.988 0 5.15 7.072 3.246 10.378-.357.62-.795 1.217-.724 1.77.073.571.477.958 1.053 1.24zm5.402 1.672c.523.55.523.646.523 3.94a535.11 535.11 0 0 0-4.434-.028l3.911-3.912zm-7.88 2.699c.111-.37.312-.705.584-.978l4.76-4.76a.291.291 0 0 1 .412 0l1.626 1.626a.291.291 0 0 1 0 .411l-4.76 4.76c-.272.273-.608.474-.978.585l-1.96.588a.219.219 0 0 1-.272-.272l.589-1.96zm9.157-6.742a.839.839 0 0 1 0 1.187l-.94.94a.28.28 0 0 1-.395 0l-1.563-1.563a.28.28 0 0 1 0-.395l.94-.94a.839.839 0 0 1 1.187 0l.771.771z"
										fill-rule="evenodd"
									></path>
								</svg>
								{{ title }}
							</div>
						</li>
					</ul>
					<!-- 切换的内容区 -->
					<div class="question-waiting">
						<div v-for="(content, index) in tabContent" v-show="cur == index" :key="index">
							<div class="question-card flex" v-for="(item, index1) in content" :key="index1">
								<a :href="'https://www.zhihu.com/question/' + item.question.id" target="_blank" class="question-title">{{ item.question.title }}</a>
								<div class="question-tool">
									<div class="question-maintool">
										<a
											href="https://www.zhihu.com/question/369002814#write"
											target="_blank"
											data-za-not-track-link="true"
											type="button"
											class="writeAnswerButton "
										>
											<span style="display: inline-flex; align-items: center;">
												​
												<svg class="Zi Zi--Edit Button-zi" fill="currentColor" viewBox="0 0 24 24" width="1.2em" height="1.2em">
													<path
														d="M4.076 16.966a4.19 4.19 0 0 1 1.05-1.76l8.568-8.569a.524.524 0 0 1 .741 0l2.928 2.927a.524.524 0 0 1 0 .74l-8.568 8.57c-.49.49-1.096.852-1.761 1.051l-3.528 1.058a.394.394 0 0 1-.49-.488l1.06-3.53zM20.558 4.83c.59.59.59 1.546 0 2.136l-1.693 1.692a.503.503 0 0 1-.712 0l-2.812-2.812a.504.504 0 0 1 0-.712l1.693-1.693a1.51 1.51 0 0 1 2.135 0l1.389 1.389z"
													></path>
												</svg>
											</span>
											写回答
										</a>
										<button type="button" class=" followAndLaterButton ">
											<svg class="Zi Zi--Plus" fill="currentColor" viewBox="0 0 24 24" width="16" height="16">
												<path
													d="M13.491 10.488s-.012-5.387 0-5.998c-.037-1.987-3.035-1.987-2.997 0-.038 1.912 0 5.998 0 5.998H4.499c-1.999.01-1.999 3.009 0 3.009s5.995-.01 5.995-.01v5.999c0 2.019 3.006 2.019 2.997 0-.01-2.019 0-5.998 0-5.998s3.996.009 6.004.009c2.008 0 2.008-3-.01-3.009h-5.994z"
													fill-rule="evenodd"
												></path>
											</svg>
											关注问题
										</button>
										<button type="button" class=" followAndLaterButton ">
											<svg class="Zi Zi--Later" fill="currentColor" viewBox="0 0 24 24" width="24" height="24">
												<path
													d="M12.004 4.15a7.85 7.85 0 1 1-5.772 13.17.85.85 0 0 1 1.25-1.153 6.15 6.15 0 1 0-1.559-5.087l1.208.343a.542.542 0 0 1 .112.996l-2.597 1.42a.542.542 0 0 1-.732-.21l-1.44-2.561a.542.542 0 0 1 .62-.787l1.182.334a7.852 7.852 0 0 1 7.728-6.465zm-.178 3.792c.385 0 .7.31.7.69l-.003 3.495 2.564 1.693c.315.207.425.671.185.977-.24.305-.69.33-.99.126 0 0-2.53-1.663-2.844-1.9-.315-.236-.315-.551-.315-.551l.003-3.84c0-.38.315-.69.7-.69z"
													fill-rule="evenodd"
												></path>
											</svg>
											稍后答
										</button>
									</div>
									<div class="question-subtool">
										<div class="question-info">
											<span>{{ item.question.answer_count }}个回答 . {{ item.question.visit_count }}个浏览</span>
										</div>
									</div>
								</div>
							</div>
							<p class="tx-center light-grey no-more">没有更多内容</p>
						</div>
					</div>
				</div>
				<div class="col-4">
					<div class="card fill-white tiny-round mb-2 shadow p-4 d-flex flex-column justify-content-around">
						<ul class="d-flex">
							<li class="fruid-col-4 tx-center link">
								<svg class="grey-icon" viewBox="0 0 24 24" width="24" height="24">
									<path
										d="M9.273 6.13c-1.103 0-1.439.064-1.782.243a1.348 1.348 0 0 0-.576.564c-.183.336-.248.664-.248 1.743v6.64c0 1.079.065 1.407.248 1.743.135.247.323.431.576.564.343.18.68.243 1.782.243h5.454c1.103 0 1.439-.064 1.782-.243.253-.133.44-.317.576-.564.183-.336.248-.664.248-1.743V8.68c0-1.079-.065-1.407-.248-1.743a1.348 1.348 0 0 0-.576-.564c-.343-.18-.68-.243-1.782-.243H9.273zm0-1.63h5.454c1.486 0 2.025.151 2.568.436.543.284.97.7 1.26 1.232.29.532.445 1.059.445 2.512v6.64c0 1.453-.155 1.98-.445 2.512-.29.531-.717.948-1.26 1.232-.543.285-1.082.436-2.568.436H9.273c-1.486 0-2.025-.151-2.568-.436a2.997 2.997 0 0 1-1.26-1.232C5.155 17.3 5 16.773 5 15.32V8.68c0-1.453.155-1.98.445-2.512.29-.531.717-.948 1.26-1.232.543-.285 1.082-.436 2.568-.436zM8.5 8.576v1.467h7V8.576h-7zm0 2.609v1.467h7v-1.467h-7zm0 2.608v1.468h4.667v-1.468H8.5z"
									></path>
								</svg>
								<p class="item">写回答</p>
							</li>
							<li class="fruid-col-4 tx-center link">
								<svg class="grey-icon" viewBox="0 0 24 24" width="24" height="24">
									<path
										d="M15.764 6.779l-3.76 3.765c-.428.43-.555.567-.667.713a1.666 1.666 0 0 0-.208.348c-.076.167-.137.344-.314.926l-.073.243.242-.074c.58-.177.757-.238.925-.314.13-.06.232-.12.347-.209.146-.112.282-.239.712-.668l3.759-3.766-.963-.964zm.963-.965l.963.965.685-.686c.167-.168.227-.263.253-.349a.187.187 0 0 0 0-.12c-.026-.086-.086-.18-.253-.348l-.148-.148c-.167-.167-.262-.228-.348-.254a.187.187 0 0 0-.12 0c-.085.026-.18.087-.347.254l-.685.686zm.87 5.471l1.702-1.705v5.549c0 1.52-.158 2.07-.455 2.626a3.096 3.096 0 0 1-1.287 1.29c-.555.297-1.105.455-2.623.455h-5.57c-1.517 0-2.068-.158-2.622-.455a3.096 3.096 0 0 1-1.287-1.29C5.158 17.2 5 16.65 5 15.13v-5.58c0-1.52.158-2.071.455-2.627a3.096 3.096 0 0 1 1.287-1.289c.554-.297 1.105-.455 2.622-.455h3.497l-1.702 1.705H9.364c-1.126 0-1.47.066-1.82.254-.258.138-.45.33-.588.59-.188.35-.254.694-.254 1.822v5.58c0 1.128.066 1.472.254 1.822.138.259.33.452.588.59.35.188.694.254 1.82.254h5.57c1.127 0 1.47-.066 1.82-.254.258-.138.45-.331.589-.59.187-.35.253-.694.253-1.822v-3.844zm1.593-7.121l.148.147c.33.33.502.616.594.918.09.301.09.61 0 .911-.092.302-.265.587-.594.917l-5.408 5.416c-.486.487-.648.635-.845.786a3.02 3.02 0 0 1-.614.37c-.226.102-.433.176-1.091.376l-.852.26a1.021 1.021 0 0 1-1.275-1.277l.26-.854c.2-.659.273-.866.375-1.092.103-.227.218-.418.369-.616.15-.197.299-.36.785-.846l5.407-5.416c.33-.33.614-.504.915-.595.301-.092.61-.092.91 0 .301.09.586.264.916.595z"
									></path>
								</svg>
								<p class="item">写文章</p>
							</li>
							<li class="fruid-col-4 tx-center link">
								<svg class="grey-icon" viewBox="0 0 24 24" width="24" height="24">
									<path
										d="M17.13 5.52V3.5h1.35v2.02h2.02v1.35h-2.02V8.9h-1.35V6.86H15.1V5.52h2.03zm-.17 4.9h1.7v4.76c0 1.5-.17 2.05-.46 2.6-.3.55-.73.98-1.28 1.27-.54.3-1.1.45-2.6.45h-5.5c-1.5 0-2.05-.16-2.6-.45-.55-.3-.98-.72-1.27-1.27-.3-.55-.45-1.1-.45-2.6v-5.5c0-1.5.16-2.06.45-2.6.3-.55.72-.98 1.27-1.28.55-.3 1.1-.45 2.6-.45h4.78v1.7H8.8c-1.12 0-1.46.05-1.8.24-.26.1-.45.3-.58.55-.2.35-.26.7-.26 1.8v5.5c0 1.13.07 1.47.26 1.8.13.27.32.46.58.6.34.18.68.25 1.8.25h5.5c1.12 0 1.46-.06 1.8-.25.27-.13.46-.32.6-.58.18-.34.24-.68.24-1.8V10.4l.02.02zm-3.86-.22c.7-.16 1.45.06 1.98.6.83.83.83 2.2 0 3.04l-.03.03c-.84.85-2.2.85-3.04 0l-1.92-2a.628.628 0 0 0-.88 0l-.04.04c-.25.28-.25.7 0 .95.15.16.37.22.57.17.4-.1.82.18.9.58.1.4-.16.82-.57.9-.7.17-1.46-.04-1.98-.58-.83-.85-.83-2.2 0-3.06l.03-.02c.86-.85 2.2-.85 3.05 0l1.93 1.95c.24.25.63.25.87 0l.03-.02a.67.67 0 0 0 0-.93.687.687 0 0 0-.58-.17c-.4.1-.8-.16-.9-.57-.1-.4.16-.8.57-.9l.01-.01z"
									></path>
								</svg>
								<p class="item">写想法</p>
							</li>
						</ul>
						<ul class="d-flex align-items-end">
							<li class="fruid-col-4 tx-center link">
								<svg class="grey-icon" viewBox="0 0 24 24" width="20" height="20">
									<path
										d="M15.375 14.74V6.75c0-1.036-.84-1.875-1.875-1.875h-9c-1.036 0-1.875.84-1.875 1.875v10.5c0 1.036.84 1.875 1.875 1.875h9c1.036 0 1.875-.84 1.875-1.875v-2.51zm2.25-7.428l1.657-1.435a2.625 2.625 0 0 1 4.343 1.985v8.276a2.625 2.625 0 0 1-4.343 1.985l-1.657-1.435v.562a4.125 4.125 0 0 1-4.125 4.125h-9A4.125 4.125 0 0 1 .375 17.25V6.75A4.125 4.125 0 0 1 4.5 2.625h9a4.125 4.125 0 0 1 4.125 4.125v.562zm0 2.976v3.424l3.13 2.71a.375.375 0 0 0 .62-.284V7.862a.375.375 0 0 0-.62-.284l-3.13 2.71z"
									></path>
								</svg>
								<p class="item">发视频</p>
							</li>
							<li class="fruid-col-4 tx-center link">
								<svg class="grey-icon" viewBox="0 0 24 24" width="24" height="24">
									<path
										d="M12.004 4.15a7.85 7.85 0 1 1-5.772 13.17.85.85 0 0 1 1.25-1.153 6.15 6.15 0 1 0-1.559-5.087l1.208.343a.542.542 0 0 1 .112.996l-2.597 1.42a.542.542 0 0 1-.732-.21l-1.44-2.561a.542.542 0 0 1 .62-.787l1.182.334a7.852 7.852 0 0 1 7.728-6.465zm-.178 3.792c.385 0 .7.31.7.69l-.003 3.495 2.564 1.693c.315.207.425.671.185.977-.24.305-.69.33-.99.126 0 0-2.53-1.663-2.844-1.9-.315-.236-.315-.551-.315-.551l.003-3.84c0-.38.315-.69.7-.69z"
										fill-rule="evenodd"
									></path>
								</svg>
								<p class="item">稍后答</p>
							</li>
							<li class="fruid-col-4 tx-center link">
								<svg class="grey-icon" viewBox="0 0 24 24" width="24" height="24">
									<path
										d="M12.917 4a2 2 0 0 1 1.478.652l4.083 4.475A2 2 0 0 1 19 10.475v5.345c0 1.453-.155 1.98-.445 2.512-.29.531-.717.948-1.26 1.232-.543.285-1.082.436-2.568.436H9.273c-1.486 0-2.025-.151-2.568-.436a2.997 2.997 0 0 1-1.26-1.232C5.155 17.8 5 17.273 5 15.82V8.18c0-1.453.155-1.98.445-2.512.29-.531.717-.948 1.26-1.232C7.248 4.15 7.787 4 9.273 4h3.644zM12 5.63H9.273c-1.103 0-1.439.064-1.782.243a1.348 1.348 0 0 0-.576.564c-.183.336-.248.664-.248 1.743v7.64c0 1.079.065 1.407.248 1.743.135.247.323.431.576.564.343.18.68.243 1.782.243h5.454c1.103 0 1.439-.064 1.782-.243.253-.133.44-.317.576-.564.183-.336.248-.664.248-1.743V11.3H14a2 2 0 0 1-2-2V5.63zm1.5.37v2.9a.9.9 0 0 0 .9.9H17L13.5 6z"
									></path>
								</svg>
								<p class="item">草稿箱</p>
							</li>
						</ul>
					</div>
					<div class="card fill-white tiny-round mb-2 shadow p-3">
						<div class="d-flex justify-content-between border-bottom pb-3">
							<div class="d-flex align-items-center">
								<svg class="grey-icon" viewBox="0 0 24 24" width="24" height="24">
									<path
										d="M15.075 15.388l-3.024 3.024a4.041 4.041 0 0 0-1.014 1.697l-.26.868C7.844 20.986 4.91 21 2 21c.026-3.325 0-3.304.59-3.956 1.237-1.368 6.251-.68 6.44-2.976.043-.518-.36-1.06-.725-1.69C6.285 8.87 5.512 2 11.5 2c5.988 0 5.15 7.072 3.246 10.378-.357.62-.795 1.217-.724 1.77.073.571.477.958 1.053 1.24zm5.402 1.672c.523.55.523.646.523 3.94a535.11 535.11 0 0 0-4.434-.028l3.911-3.912zm-7.88 2.699c.111-.37.312-.705.584-.978l4.76-4.76a.291.291 0 0 1 .412 0l1.626 1.626a.291.291 0 0 1 0 .411l-4.76 4.76c-.272.273-.608.474-.978.585l-1.96.588a.219.219 0 0 1-.272-.272l.589-1.96zm9.157-6.742a.839.839 0 0 1 0 1.187l-.94.94a.28.28 0 0 1-.395 0l-1.563-1.563a.28.28 0 0 1 0-.395l.94-.94a.839.839 0 0 1 1.187 0l.771.771z"
										fill-rule="evenodd"
									></path>
								</svg>
								<p class="meta ml-2 normal-font">
									创作者中心
									<span class="blue ml-3 normal-font">去开通</span>
								</p>
							</div>

							<svg class="grey-icon" style="margin-top:12px ;" viewBox="0 0 24 24" width="24" height="24">
								<path
									d="M9.218 16.78a.737.737 0 0 0 1.052 0l4.512-4.249a.758.758 0 0 0 0-1.063L10.27 7.22a.737.737 0 0 0-1.052 0 .759.759 0 0 0-.001 1.063L13 12l-3.782 3.716a.758.758 0 0 0 0 1.063z"
									fill-rule="evenodd"
								></path>
							</svg>
						</div>
						<div class="row p-3 border-bottom">
							<div class="col-6 tx-center">
								<p class="meta">昨日被阅读数</p>
								<h3>0</h3>
								<p class="meta">较前日--</p>
							</div>
							<div class="col-6 tx-center">
								<p class="meta">昨日获赞同数</p>
								<h3>0</h3>
								<p class="meta">较前日--</p>
							</div>
						</div>
					</div>

					<div class="card fill-white tiny-round mb-2 shadow p-3 d-flex flex-column justify-content-around">
						<ul class="d-flex">
							<li class="fruid-col-4 tx-center link">
								<svg class="live-icon" viewBox="0 0 24 24" width="24" height="24">
									<path
										d="M13.693 10.354l1.634-7.542c.195-.901-.16-1.083-.798-.39l-9.18 9.97c-.638.693-.377 1.254.582 1.254h5.376l-1.634 7.542c-.195.901.16 1.083.798.39l9.18-9.97c.638-.693.377-1.254-.582-1.254h-5.376z"
									></path>
								</svg>
								<p class="light-grey">LIVE</p>
							</li>
							<li class="fruid-col-4 tx-center link">
								<svg class="bookshop-icon" viewBox="0 0 24 24" width="24" height="24">
									<path
										d="M16 17.649V2.931a.921.921 0 0 0-.045-.283.943.943 0 0 0-1.182-.604L4.655 5.235A.932.932 0 0 0 4 6.122v14.947c0 .514.421.931.941.931H19.06c.52 0 .941-.417.941-.93V7.292a.936.936 0 0 0-.941-.931h-.773v12.834a.934.934 0 0 1-.83.924L6.464 21.416c-.02.002 2.94-.958 8.883-2.881a.932.932 0 0 0 .653-.886z"
										fill-rule="evenodd"
									></path>
								</svg>
								<p class="light-grey">书店</p>
							</li>
							<li class="fruid-col-4 tx-center link">
								<svg class="roundtable-icon" viewBox="0 0 24 24" width="24" height="24">
									<path
										d="M10.786 8.41a8.938 8.938 0 0 0-3.968-2.528c-.305-1.719.814-3.337 2.442-3.741 1.221-.405 2.646.101 3.46 1.011 1.045 1.38.915 3.64.814 4.348-.102 1.315-1.221 3.034-1.323 3.135-.305-.809-.814-1.517-1.425-2.225zm-2.442 2.832c-1.526.202-3.052 1.01-4.171 2.123-1.12-.404-1.934-1.314-2.137-2.427-.316-2.427 1.526-3.64 2.849-3.842 1.628-.371 2.849.505 4.07 1.415 1.146 1.012 2.035 2.63 2.035 2.73-.916-.202-1.832-.1-2.646 0zm4.986.303c.509-.607.931-1.586 1.12-2.225.318-1.039.61-3.134.203-4.651 1.323-1.011 3.154-1.011 4.477.303 1.235 1.146 1.017 2.933.814 3.438-.663 1.581-1.933 2.326-3.256 2.832-1.221.404-3.256.303-3.358.303zm-2.645 1.011c-.51.607-.916 1.416-1.221 2.326-.407 1.314-.643 3.06-.102 4.55-1.323 1.011-3.256 1.011-4.477-.202-1.198-1.124-1.018-2.932-.814-3.438.599-1.605 1.933-2.326 3.256-2.831.916-.304 3.256-.405 3.358-.405zm9.259-1.82c1.017.404 1.933 1.315 2.035 2.427.233 2.57-1.526 3.64-2.849 3.842-1.526 0-2.85-.505-4.07-1.415-1.018-.81-2.035-2.528-2.035-2.63.916.203 1.831.102 2.645 0 1.628-.404 3.053-1.112 4.274-2.224zm-6.716 4.854c1.065 1.08 2.442 2.022 4.07 2.528.306 1.719-.814 3.235-2.442 3.741-1.22.405-2.645-.101-3.46-1.011-1.1-1.481-1.017-3.54-.915-4.247.102-1.315 1.221-3.034 1.323-3.135.305.708.721 1.44 1.424 2.124z"
									></path>
								</svg>
								<p class="light-grey">圆桌</p>
							</li>
						</ul>
						<ul class="d-flex">
							<li class="fruid-col-4 tx-center link">
								<svg class="column-icon" viewBox="0 0 24 24" width="24" height="24">
									<path
										d="M4.076 16.966a4.19 4.19 0 0 1 1.05-1.76l8.568-8.569a.524.524 0 0 1 .741 0l2.928 2.927a.524.524 0 0 1 0 .74l-8.568 8.57c-.49.49-1.096.852-1.761 1.051l-3.528 1.058a.394.394 0 0 1-.49-.488l1.06-3.53zM20.558 4.83c.59.59.59 1.546 0 2.136l-1.693 1.692a.503.503 0 0 1-.712 0l-2.812-2.812a.504.504 0 0 1 0-.712l1.693-1.693a1.51 1.51 0 0 1 2.135 0l1.389 1.389z"
									></path>
								</svg>
								<p class="light-grey">专栏</p>
							</li>
							<li class="fruid-col-4 tx-center link">
								<svg class="consult-icon" viewBox="0 0 24 24" width="24" height="24">
									<path
										d="M11.267 10.188h-2.69a.26.26 0 0 0-.261.26v.508c0 .149.117.26.262.26h2.896v1.54H8.578a.26.26 0 0 0-.262.259v.508c0 .15.117.26.262.26h2.896v2.31c0 .139.119.257.265.257h.522a.258.258 0 0 0 .265-.257v-2.31h2.896a.26.26 0 0 0 .262-.26v-.508a.257.257 0 0 0-.262-.26h-2.896v-1.54h2.896a.26.26 0 0 0 .262-.26v-.507a.257.257 0 0 0-.262-.26h-2.69l2.51-2.636a.26.26 0 0 0-.004-.366l-.423-.413a.253.253 0 0 0-.36.01L12 9.418 9.545 6.784a.248.248 0 0 0-.36-.011l-.423.413a.264.264 0 0 0-.004.366l2.509 2.636zM12 19.973c-1.101 0-2.16-.15-3.152-.43-.532.18-5.27 2.177-4.743 1.179.527-.998 1.58-2.746.806-3.25C3.11 15.936 2 13.822 2 11.486 2 6.8 6.477 3 12 3s10 3.8 10 8.487-4.477 8.486-10 8.486z"
									></path>
								</svg>
								<p class="light-grey">付费咨询</p>
							</li>
							<li class="fruid-col-4 tx-center link">
								<svg class="wiki-icon" viewBox="0 0 24 24" width="24" height="24">
									<path
										d="M21 9.749v9.91c0 .74-.604 1.341-1.35 1.341H4.35C3.604 21 3 20.4 3 19.659V9.319c0-.503.283-.963.733-1.193l4.892-2.5V3.341c0-.74.604-1.341 1.35-1.341.267 0 .527.078.749.225l9.675 6.408c.375.249.601.668.601 1.116zM8.297 8.307L5.372 9.802A.223.223 0 0 0 5.25 10v8.54c0 .124.1.224.225.224h8.586a.223.223 0 1 0 .124-.41l-4.959-3.259a1.339 1.339 0 0 1-.601-1.116V8.506a.224.224 0 0 0-.328-.199z"
									></path>
								</svg>
								<p class="light-grey">百科</p>
							</li>
						</ul>
					</div>

					<div class="cardTwo fill-white tiny-round mb-2 shadow p-3">
						<div class="d-flex p-2 justify-content-between">
							<div class="d-flex  align-items-end">
								<svg class="grey-icon" viewBox="0 0 24 24" width="18" height="18">
									<path
										d="M5.515 19.64l.918-5.355-3.89-3.792c-.926-.902-.639-1.784.64-1.97L8.56 7.74l2.404-4.871c.572-1.16 1.5-1.16 2.072 0L15.44 7.74l5.377.782c1.28.186 1.566 1.068.64 1.97l-3.89 3.793.918 5.354c.219 1.274-.532 1.82-1.676 1.218L12 18.33l-4.808 2.528c-1.145.602-1.896.056-1.677-1.218z"
										fill-rule="evenodd"
									></path>
								</svg>
								<span class="light-grey link ml-2">我的收藏</span>
							</div>
							<span class="number-icon">0</span>
						</div>

						<div class="d-flex p-2 justify-content-between">
							<div class="d-flex  align-items-end">
								<svg class="grey-icon" viewBox="0 0 24 24" width="18" height="18">
									<path
										d="M5.74 4h12.52c.961 0 1.74.775 1.74 1.73V16.27c0 .955-.779 1.73-1.74 1.73h-3.825l-1.658 2.044a1 1 0 0 1-1.554 0l-1.658-2.044H5.74C4.78 18 4 17.224 4 16.27V5.73C4 4.775 4.778 4 5.74 4zM12 16a.976.976 0 0 0 .705-.287.951.951 0 0 0 .295-.712.954.954 0 0 0-.295-.714A.976.976 0 0 0 12 14a.962.962 0 0 0-.705.295A.961.961 0 0 0 11 15c0 .284.098.522.295.713A.975.975 0 0 0 12 16zm1.278-4.924a36.81 36.81 0 0 0 1.023-.975c.19-.193.354-.422.492-.688.138-.266.207-.575.207-.928 0-.448-.12-.864-.363-1.246a2.517 2.517 0 0 0-1.029-.906C13.164 6.111 12.652 6 12.072 6c-.624 0-1.17.133-1.638.399-.468.265-.824.6-1.068 1.005-.244.405-.366.804-.366 1.2 0 .19.077.368.231.531a.747.747 0 0 0 .567.246c.38 0 .638-.234.774-.703.144-.449.32-.788.528-1.019.208-.23.532-.345.972-.345.376 0 .683.114.921.342.238.229.357.51.357.841 0 .17-.039.328-.117.473a1.782 1.782 0 0 1-.288.396c-.114.118-.3.294-.555.526a9.71 9.71 0 0 0-.696.688c-.172.194-.31.418-.414.673a2.391 2.391 0 0 0-.156.906c0 .278.071.488.213.63a.716.716 0 0 0 .525.211c.4 0 .638-.216.714-.648.044-.203.077-.345.099-.426.022-.081.053-.162.093-.243.04-.081.101-.17.183-.268.082-.098.191-.21.327-.34z"
										fill-rule="evenodd"
									></path>
								</svg>
								<span class="light-grey link ml-2">我关注的问题</span>
							</div>
							<span class="number-icon">5</span>
						</div>

						<div class="d-flex p-2 justify-content-between">
							<div class="d-flex  align-items-end">
								<svg class="grey-icon" viewBox="0 0 24 24" width="18" height="18">
									<path
										d="M4 10V8a1 1 0 1 1 2 0v2h2a1 1 0 0 1 0 2H6v2a1 1 0 0 1-2 0v-2H2a1 1 0 0 1 0-2h2zm10.455 2c-2.21 0-4-1.79-4-4s1.79-4 4-4 4 1.79 4 4-1.79 4-4 4zm-7 6c0-2.66 4.845-4 7.272-4C17.155 14 22 15.34 22 18v1.375c0 .345-.28.625-.625.625H8.08a.625.625 0 0 1-.625-.625V18z"
										fill-rule="evenodd"
									></path>
								</svg>
								<span class="light-grey link ml-2">我的邀请</span>
							</div>
							<span class="number-icon">121</span>
						</div>

						<div class="d-flex p-2 justify-content-between">
							<div class="d-flex  align-items-end">
								<svg class="grey-icon" viewBox="0 0 24 24" width="18" height="18">
									<path
										d="M19 19.5H5a2 2 0 0 1-2-2V7a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2v10.5a2 2 0 0 1-2 2zm0-12a.5.5 0 0 0-.5-.5h-13a.5.5 0 0 0-.5.5v2a.5.5 0 0 0 .5.5h3.75c1 0 1 2 2.75 2s1.75-2 2.75-2h3.75a.5.5 0 0 0 .5-.5v-2z"
										fill-rule="evenodd"
									></path>
								</svg>
								<span class="light-grey link ml-2">我的余额</span>
							</div>
							<span class="number-icon">0</span>
						</div>

						<div class="d-flex p-2 justify-content-between">
							<div class="d-flex  align-items-end">
								<svg class="grey-icon" viewBox="0 0 24 24" width="18" height="18">
									<path
										d="M5.74 4h12.52c.961 0 1.74.775 1.74 1.73V16.27c0 .955-.779 1.73-1.74 1.73h-3.825l-1.658 2.044a1 1 0 0 1-1.554 0l-1.658-2.044H5.74C4.78 18 4 17.224 4 16.27V5.73C4 4.775 4.778 4 5.74 4zM7 8.98c0 .554.449.996 1.003.996h4.994A.992.992 0 0 0 14 8.981a.997.997 0 0 0-1.003-.995H8.003A.992.992 0 0 0 7 8.98zm0 4c0 .554.446.996.995.996h8.01a.993.993 0 0 0 .995-.995.993.993 0 0 0-.995-.995h-8.01A.993.993 0 0 0 7 12.98z"
										fill-rule="evenodd"
									></path>
								</svg>
								<span class="light-grey link ml-2">站务中心</span>
							</div>
						</div>

						<div class="d-flex p-2 justify-content-between">
							<div class="d-flex  align-items-end">
								<svg class="grey-icon" viewBox="0 0 24 24" width="18" height="18">
									<path
										d="M16.517 15.815a5.871 5.871 0 0 1-4.481 2.078 5.865 5.865 0 0 1-5.859-5.857 5.865 5.865 0 0 1 5.859-5.859c1.63 0 3.204.7 4.319 1.919.085.093.24.432.209.797a1.086 1.086 0 0 1-.436.779c-.248.193-.516.29-.797.29-.402 0-.7-.198-.814-.314A3.473 3.473 0 0 0 12 8.575a3.464 3.464 0 0 0-3.46 3.461 3.464 3.464 0 0 0 3.46 3.46 3.63 3.63 0 0 0 2.654-1.181c.136-.152.458-.306.806-.306.274 0 .542.095.773.274.35.269.45.588.473.809.032.308-.072.585-.188.723m4.686-7.699C20.67 6.883 19.96 5.82 19.07 4.929c-.891-.89-1.954-1.601-3.188-2.133A9.728 9.728 0 0 0 12 2a9.733 9.733 0 0 0-3.883.796c-1.234.532-2.297 1.243-3.186 2.133-.891.891-1.602 1.954-2.134 3.187A9.713 9.713 0 0 0 2 12a9.752 9.752 0 0 0 .797 3.883c.531 1.233 1.242 2.296 2.134 3.186.89.891 1.953 1.602 3.186 2.134A9.725 9.725 0 0 0 12 22a9.72 9.72 0 0 0 3.883-.797c1.233-.532 2.296-1.243 3.188-2.134.89-.89 1.601-1.953 2.132-3.186A9.73 9.73 0 0 0 22 12a9.69 9.69 0 0 0-.797-3.884"
										fill-rule="evenodd"
									></path>
								</svg>
								<span class="light-grey link ml-2">版权服务中心</span>
							</div>
						</div>
					</div>

					<div class="card-one">
						<div class="d-flex p-2 justify-content-around footer-item">
							<li>刘看山</li>
							<li>知乎指南</li>
							<li>知乎协议</li>
							<li>知乎隐私保护指引</li>
						</div>
						<div class="d-flex p-2  footer-item">
							<li class="ml-1">应用</li>
							<li class="ml-2">工作</li>
							<li class="ml-2">申请开通知乎机构号</li>
						</div>
						<div class="d-flex p-2  footer-item">
							<li class="ml-1">侵权举报</li>
							<li class="ml-2">网上有害信息举报专区</li>
						</div>
						<div class="d-flex p-2  footer-item"><li class="ml-1">京ICP证 1104745号</li></div>
						<div class="d-flex p-2  footer-item"><li class="ml-1">京ICP备 13052560号-1</li></div>
						<div class="d-flex p-2  footer-item">
							<img src="https://pic3.zhimg.com/80/v2-d0289dc0a46fc5b15b3363ffa78cf6c7.png" />
							<li class="ml-1">京公网安备 11010802010035号</li>
						</div>
						<div class="d-flex p-2  footer-item"><li class="ml-1">互联网药品信息服务资格证书</li></div>
						<div class="d-flex p-2  footer-item"><li>（京）-非经营性-2017-0067</li></div>
						<div class="d-flex p-2  footer-item"><li class="ml-1">违法和不良信息举报：010-82716601</li></div>
						<div class="d-flex p-2  footer-item"><li class="ml-1">证照中心</li></div>
						<div class="d-flex p-2  footer-item"><li class="ml-1">联系我们@2020知乎</li></div>
					</div>
				</div>
			</div>
		</div>
		<button class="goto-top" @click="backToTop" v-show="btnFlag">
			<svg class="grey-icon" title="回到顶部" viewBox="0 0 24 24" width="24" height="24">
				<path
					d="M16.036 19.59a1 1 0 0 1-.997.995H9.032a.996.996 0 0 1-.997-.996v-7.005H5.03c-1.1 0-1.36-.633-.578-1.416L11.33 4.29a1.003 1.003 0 0 1 1.412 0l6.878 6.88c.782.78.523 1.415-.58 1.415h-3.004v7.005z"
				></path>
			</svg>
		</button>
	</div>
</template>

<script>
export default {
	name: 'questionWaiting',
	data() {
		return {
			tabTitle: ['人气问题', '潜力好问', '新问题', '人人答'],
			category: ['hot', 'potential', 'new', 'people'],
			tabContent: [[], [], [], []],
			cur: 0,
			btnFlag: false
		};
	},
	mounted() {
		// window对象，所有浏览器都支持window对象。它表示浏览器窗口，监听滚动事件
		window.addEventListener('scroll', this.scrollToTop);
	},
	created() {
		this.axios.get('/api/question/waiting/hot').then(res => {
			this.tabContent.splice(0, 0, res.data.data.data);
		});
	},
	methods: {
		change(index) {
			this.cur = index;
			//取出对应的参数数组的值
			let param = this.category[index];
			//发起对应请求
			this.axios.get('/api/question/waiting/' + param).then(res => {
				this.tabContent.splice(index, 0, res.data.data.data);
			});
			if (param == 'hot') {
				this.$router.push('/question/waiting');
			} else {
				this.$router.push('/question/waiting?type=' + param);
			}
		},
		backToTop() {
			//加定时器，平滑过渡回到顶部
			let timer = setInterval(() => {
				let ispeed = Math.floor(-this.scrollTop / 5);
				document.documentElement.scrollTop = document.body.scrollTop = this.scrollTop + ispeed;
				if (this.scrollTop === 0) {
					clearInterval(timer);
				}
			}, 16);
		},
		scrollToTop() {
			let scrollTop = window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop;
			this.scrollTop = scrollTop;
			if (this.scrollTop > 500) {
				this.btnFlag = true;
			} else {
				this.btnFlag = false;
			}
		}
	}
};
</script>

<style lang="scss" scoped>
.col-8 {
	flex: 0 0 80%;
	margin-left: -160px;
	/*tab切换*/
	.tab-title {
		display: flex;
		align-items: center;
		height: 63px;
		padding: 0.625rem;
		background-color: #fff;
		.tab-info {
			align-items: center;
			background: rgba(133, 144, 166, 0.12);
			border-radius: 16px;
			box-shadow: 0 6px 10px 0 rgba(133, 144, 166, 0.06);
			cursor: pointer;
			display: flex;
			font-size: 14px;
			padding: 0 12px;
			height: 32px;
			line-height: 32px;
			svg {
				margin-right: 2px;
				color: #8590a6;
			}
		}
		li {
			width: 100px;
			height: 30px;
			line-height: 30px;
			text-align: center;
			border-radius: 20px;
			margin: 8px;
			background-color: #f6f6f6;
			color: #646464;
			cursor: pointer;
		}
		.active {
			background-color: #e6f3ff;
			color: #0c89ff;
		}
	}
}
.no-more:before,
.no-more:after {
	content: '';
	display: inline-block;
	width: 24px;
	height: 1px;
	margin: 0 10px;
	vertical-align: middle;
	background-color: #d3d3d3;
}
.light-grey {
	margin: 0;
	color: #8590a6;
	text-align: center;
	background-color: transparent;
	margin-left: 24px;
	font-size: 14px;
	padding: 0;
	.grey-icon {
		fill: #8590a6;
	}
}
.question-waiting {
	padding: 0 20px;
	background-color: #fff;
}
.question-card {
	display: flex;
	flex-direction: column;
	align-items: flex-start;
	padding: 17px 0 22px;
	position: relative;
	border-bottom: 1px solid #f6f6f6;
	.question-title {
		color: #1a1a1a;
		font-size: 18px;
		line-height: 27px;
		font-weight: 600;
		margin-bottom: 0;
		margin-right: 26px;
	}
	.question-tool {
		margin-top: 17px;
		align-items: center;
		display: flex;
		.question-subtool {
			align-items: center;
			display: flex;
			margin-left: auto;
			.question-info {
				color: #8590a6;
				font-size: 14px;
				margin-left: 200px;
			}
		}
		.question-maintool {
			align-items: center;
			display: flex;
			.writeAnswerButton {
				display: inline-block;
				font-size: 14px;
				text-align: center;
				cursor: pointer;
				background: none;
				border: 1px solid;
				border-radius: 3px;
				color: #0084ff;
				border-color: #0084ff;
				line-height: 28px;
				padding: 0;
				width: 94px;
			}
			.followAndLaterButton {
				margin: 0;
				font-size: 14px;
				text-align: center;
				cursor: pointer;
				background: none;
				color: #8590a6;
				height: auto;
				padding: 0;
				background-color: transparent;
				border: none;
				border-radius: 0;
				align-items: center;
				display: flex;
				line-height: 28px;
				justify-content: center;
				width: 96px;
				margin-left: 20px;
			}
		}
	}
}
.card {
	width: 300px;
	height: 200px;
	border: 1px solid #eee;
	/* 圆角边框 */
	border-radius: 2px;
	/* margin是指从自身边框到另一个容器边框之间的距离，就是容器外距离 */
	margin: 0px;
	/* padding是指自身边框到自身内部另一个容器边框之间的距离，就是容器内距离 */
	padding: 10px;
	margin-left: 10px;
	margin-bottom: 10px;
}
.goto-top {
	position: fixed;
	right: 30px;
	bottom: 30px;
	width: 40px;
	height: 40px;
	background: #fff;
	border: 1px solid #eee;
	border-radius: 3px;
	cursor: pointer;
}
// 各种彩色图标填充色
.live-icon {
	fill: #fecc00;
}
.bookshop-icon {
	fill: #53d37e;
}
.roundtable-icon {
	fill: #0c89ff;
}
.column-icon {
	fill: #1a8cee;
}
.consult-icon {
	fill: #537df3;
}
.wiki-icon {
	fill: #576cd3;
}
// 数字样式
.number-icon {
	font-size: 12px;
	padding: 4px 10px;
	background-color: #f6f6f6;
	color: #8590a6;
}
.footer-item {
	font-size: 13px;
	color: #8590a6;
	width: 100%;
	li {
		display: inline;
	}
}
</style>
