<template>
	<div class="dashboard">
		<b-container>
			<h1 class="mt-5 text-left">Dashboard for {{ hashtag }}</h1>
			<hr />
			<b-row class="mt-1 mb-5">
				<b-col cols="3">
					<b-card sub-title="Number Of Tweets">
						<b-card-text>
							<h1>{{ count }}</h1>
						</b-card-text>
						<b-link to="/tweets/vaksin">
							<a>details</a>
						</b-link>
					</b-card>
				</b-col>
				<b-col cols="3">
					<b-card sub-title="Positive Sentiments">
						<b-card-text>
							<h1>{{ positiveSentiment }}</h1>
						</b-card-text>
						<b-link to="/positive-tweets/vaksin">
							<a>details</a>
						</b-link>
					</b-card>
				</b-col>
				<b-col cols="3">
					<b-card sub-title="Negative Sentiments">
						<b-card-text>
							<h1>{{ negativeSentiment }}</h1>
						</b-card-text>
						<b-link to="/negative-tweets/vaksin">
							<a>details</a>
						</b-link>
					</b-card>
				</b-col>
				<b-col cols="3">
					<b-card sub-title="Accuracy">
						<b-card-text>
							<h1>82.45%</h1>
						</b-card-text>
						<b-link to="/accuracy-model">
							<a>details</a>
						</b-link>
					</b-card>
				</b-col>
			</b-row>
			<div class="mb-5">
				<line-chart v-if="hashtag" :hashtag="hashtag" />
			</div>
			<b-row class="mt-5">
				<b-col cols="5">
					<pie-chart v-if="posneg" :data="posneg" />
				</b-col>
				<b-col cols="7">
					<div>
						<b-card no-body>
							<b-tabs card>
								<b-tab title="Positive" active>
									<img src="../assets/wordcloud-positive.png" width="100%"/>
									<!-- <word-cloud :data="defaultWords" nameKey="name" valueKey="value" color="Accent" /> -->
								</b-tab>
								<b-tab title="Negative">
									<img src="../assets/wordcloud-negative.png" width="100%"/>
									<!-- <word-cloud :data="defaultWords" nameKey="name" valueKey="value" color="Accent" /> -->
								</b-tab>
							</b-tabs>
						</b-card>
					</div>

				</b-col>
			</b-row>
			<b-row class="mt-5">
				<!-- <b-col cols="7"> -->
				<top-tweets v-if="hashtag" :hashtag="hashtag" />
				<!-- </b-col> -->
			</b-row>
		</b-container>
	</div>
</template>

<script>
import LineChart from '@/components/LineChart.vue';
import PieChart from '@/components/PieChart.vue';
import TopTweets from '@/components/TopTweets.vue';
// import WordClound from '@/components/WordClound.vue';
import axios from "axios";

export default {
	name: 'Dashboard',
	components: {
		'line-chart': LineChart,
		'pie-chart': PieChart,
		// 'word-cloud': WordClound,
		'top-tweets': TopTweets,
	},
	data() {
		return {
			count: null,
			positiveSentiment: null,
			negativeSentiment: null,
			hashtag: null,
			posneg: null,
		}
	},
	created() {
		this.hashtag = this.$route.params.hashtag;
		this.countTweet();
		this.countSentiment();
	},
	methods: {
		countTweet: function () {
			let url = "https://be-sentiment-app-ta.herokuapp.com/tweet/count?hashtag=" + this.hashtag;
			axios
				.get(url)
				.then(
					function (response) {
						console.log(response);
						this.count = response.data.count
					}.bind(this)
				)
				.catch(function (error) {
					console.log(error)
				});
		},
		countSentiment: function () {
			let url = "https://be-sentiment-app-ta.herokuapp.com/tweet/sentiment?hashtag=" + this.hashtag;
			axios
				.get(url)
				.then(
					function (response) {
						console.log("a", response);
						for (let i = 0; i < response.data.result.length; i++) {
							if (response.data.result[i].label == 0) {
								this.negativeSentiment = response.data.result[i].result;
							} else {
								this.positiveSentiment = response.data.result[i].result;
							}
						}
						this.posneg = [this.positiveSentiment, this.negativeSentiment];
					}.bind(this)
				)
				.catch(function (error) {
					console.log(error)
				});
		}
	}
}
</script>