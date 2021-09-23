<template>
	<div id="app">
		<img alt="Vue logo" src="./assets/logo.png" />
		<div>
			<label for="">
				Hide
				<input type="checkbox" v-model="hideForm" />
			</label>
		</div>
		<DiaryForm v-show="!hideForm" @add="addDiaryEntry" />
	</div>
</template>

<script>
import DiaryForm from './components/DiaryForm.vue';

export default {
	name: 'App',
	components: {
		DiaryForm,
		// ToggleShowForm,
	},
	methods: {
		addDiaryEntry(diaryObject) {
			console.log('diaryObject: ', diaryObject);
			this.diaryEntries.unshift(diaryObject);
			console.log('diaryEntries: ', this.diaryEntries);
			console.log('diaryEntries: ', typeof this.diaryEntries);
		},
	},
	data() {
		return {
			diaryEntries: [],
			hideForm: true,
		};
	},
};
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}

p {
	white-space: pre-line;
}
</style>
