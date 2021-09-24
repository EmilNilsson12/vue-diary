<template>
	<div id="app">
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
			console.log('diaryObject: ', diaryObject);
			this.diaryEntriesArr.unshift(diaryObject);
			this.diaryEntriesArr = [...this.diaryEntriesArr].sort(
				this.compareByDates
			);
			console.log('diaryEntries: ', this.diaryEntriesArr);
		},
		compareByDates(a, b) {
			console.log('a: ', a);
			console.log('b: ', b);
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
			buttonValueHistory: [],
			hideForm: true,
			buttonValue: 0,
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
