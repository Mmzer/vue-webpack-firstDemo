<template>
	<style>
		.form-margin-bottom{
			margin-bottom: 15px;
		}
	</style>
	<div class="form-horizontal form-margin-bottom">
		<div class="form-group">
			<div class="col-sm-6">
				<label>日期</label>
				<input
					type="date"
					class="form-control"
					v-model="timeEntry.date"
					placeholder="Date"/>
			</div>
			<div class="col-sm-6">
				<label>时间</label>
				<input
					type="number"
					class="form-control"
					v-model="timeEntry.totalTime"
					placeholder="Hours"/>
			</div>
			<div class="col-sm-6">
				<label>备注</label>
				<input
					type="text"
					class="form-control"
					v-model="timeEntry.comment"
					placeholder="Comment"/>
			</div>
		</div>
		<button class="btn btn-primary" @click="save()">保存</button>
		<button class="btn btn-danger" v-link="'/time-entries'">取消</button>
	</div>
</template>

<script>
	export default{
		data () {
			return {
				timeEntry: {
					user: {
						name: 'Mmzer',
						email: 'mmzer@qq.com',
						image: 'https://avatars2.githubusercontent.com/u/9158841?v=3&s=460'
					}
				}
			}
		},

		methods: {
			save () {
				let timeEntry = this.timeEntry
				this.$dispatch('timeUpdate', timeEntry)
				this.timeEntry = {}
			}
		}
	}
</script>