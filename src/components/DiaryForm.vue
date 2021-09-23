<template>
	<div>
		<form @submit.prevent="handleSubmit">
			<p>
				<label for="diaryTitle">
					Title
					<input
						type="text"
						name="diaryTitle"
						id="diaryTitle"
						v-model="diaryTitle"
						required
					/>
				</label>
			</p>
			<p>
				<label for="diaryBody">
					Story
					<textarea
						name="diaryBody"
						id="diaryBody"
						v-model="diaryBody"
						required
					/>
				</label>
			</p>
			<p>
				<label for="diaryBody">
					Story
					<input
						type="date"
						name="diaryBody"
						id="diaryBody"
						v-model="diaryDate"
						required
					/>
				</label>
			</p>
			<p><button type="submit">Done!</button></p>
		</form>
		<Preview :title="diaryTitle" :body="diaryBody" :date="diaryDate" />
	</div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';
import Preview from './Preview.vue';

export default {
	name: 'DiaryForm',
	props: {
		msg: String,
	},
	components: {
		Preview,
	},
	methods: {
		handleSubmit(evt) {
			console.log('Submitted!');
			console.log(evt.target);

			this.$emit('add', {
				diaryId: uuidv4(),
				diaryTitle: this.diaryTitle,
				diaryBody: this.diaryBody,
				diaryDate: this.diaryDate,
			});
		},
	},
	data() {
		return {
			diaryTitle: '',
			diaryBody: '',
			diaryDate: '',
		};
	},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
	margin: 40px 0 0;
}
ul {
	list-style-type: none;
	padding: 0;
}
li {
	display: inline-block;
	margin: 0 10px;
}
a {
	color: #42b983;
}
</style>
