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
		<DiaryEntries />
		<button v-on:click="myFunc">button w {{ buttonValue }}</button>
		<div v-if="buttonValueHistory.length > 0">
			<div
				v-for="number in buttonValueHistory"
				:key="number + '_key'"
				:style="getWrapperStyle()"
			>
				<div :style="getStyle(number)"></div>
			</div>
		</div>
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
		// ToggleShowForm,
	},
	methods: {
		addDiaryEntry(diaryObject) {
			console.log('diaryObject: ', diaryObject);
			this.diaryEntries.unshift(diaryObject);
			console.log('diaryEntries: ', this.diaryEntries);
			console.log('diaryEntries: ', typeof this.diaryEntries);
		},
		myFunc() {
			if (this.buttonValue < 630) {
				this.buttonValue = this.buttonValue * 2 + 7;
			} else {
				this.buttonValue = parseInt(this.buttonValue / 5, 10);
			}
			this.buttonValueHistory.unshift(this.buttonValue);
			console.log('buttonValueHistory: ', this.buttonValueHistory);
		},
		getWrapperStyle() {
			return `
				width: 100%;
				display: flex;
				justify-content: center;
				align-items: center;
			`;
		},
		getStyle(num) {
			return `
				width: ${num}px;
				min-width: 20px;
				height: 20px;
				background-color: hsl(${num * 3}deg, 50%, 50%);
			`;
		},
	},
	data() {
		return {
			diaryEntries: [],
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
