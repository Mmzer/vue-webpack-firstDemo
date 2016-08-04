<template>
	<div id="wrapper">
		<nav class="navbar navbar-default">
			<div id="container">
				<a href="#" class="navbar-brand">
					<i class="glyphicon glyphicon-time"></i>
					计划表
				</a>
				<ul class="nav navbar-nav">
					<li><a v-link="'/home'">首页</a></li>
					<li><a v-link="'/time-entries'">计划列表</a></li>
				</ul>
			</div>
		</nav>
		<div id="container">
			<div class="col-sm-3">
				<slidebar :time="totalTime"></slidebar>
			</div>
			<div class="col-sm-9">
		    	<router-view></router-view>
		    </div>
		</div>
	</div>
</template>

<script>
	import Slidebar from './components/Slidebar.vue'

	export default {
		components: {
			'slidebar': Slidebar
		},

		data () {
			return {
				totalTime: 1.5
			}
		},

		events: {
			timeUpdate (timeEntry) {
				this.totalTime += parseFloat(timeEntry.totalTime)
			},
			deleteTime (timeEntry) {
				this.totalTime -= parseFloat(timeEntry.totalTime)
			}
		}
	}
</script>