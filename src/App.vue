<template>
	<div id="app">
		<h1>Vue Diary App</h1>
		<img alt="Vue logo" src="./assets/logo.png" />
		<div>
			<label for="toggleForm">
				Hide form
				<input type="checkbox" id="toggleForm" v-model="hideForm" />
			</label>
		</div>
		<DiaryForm v-show="!hideForm" @add="addDiaryEntry" />
		<DiaryEntries :entries="diaryEntriesArr" />
	</div>
</template>

<script>
import DiaryForm from './components/DiaryForm.vue';
import DiaryEntries from './components/DiaryEntries.vue';

export default {
	name: 'App',
	components: {
		DiaryForm,
		DiaryEntries,
	},
	methods: {
		addDiaryEntry(diaryObject) {
			this.diaryEntriesArr.unshift(diaryObject);
			this.diaryEntriesArr = [...this.diaryEntriesArr].sort(
				this.compareByDates
			);
			localStorage.setItem(
				'diaryEntries',
				JSON.stringify(this.diaryEntriesArr)
			);
		},
		compareByDates(a, b) {
			const aDate = new Date(a.diaryDate);
			const bDate = new Date(b.diaryDate);

			let returnValue;
			aDate < bDate
				? (returnValue = 1)
				: aDate > bDate
				? (returnValue = -1)
				: (returnValue = 0);

			return returnValue;
		},
	},
	data() {
		return {
			diaryEntriesArr: [],
			hideForm: true,
			buttonValue: 0,
		};
	},
	/* eslint-disable no-mixed-spaces-and-tabs */
	mounted() {
		localStorage.getItem('diaryEntries')
			? (this.diaryEntriesArr = [
					...JSON.parse(localStorage.getItem('diaryEntries')),
			  ])
			: localStorage.setItem('diaryEntries', JSON.stringify([]));
	},
	/* eslint-disable no-mixed-spaces-and-tabs */
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
