<template>
	<div>
		Inside
		<div>Diary entries!</div>
		<div
			v-for="entry in entries"
			:key="entry.diaryTitle"
			class="diary-entry-format"
		>
			<h2>
				{{ entry.diaryTitle }} <span>{{ entry.diaryDate }}</span>
			</h2>
			<p>
				{{ entry.diaryBody }}
			</p>
		</div>
	</div>
</template>

<script>
export default {
	name: 'DiaryEntries',
	props: {
		entries: Array,
	},
};
</script>

<style scoped>
div {
	border: 1px solid black;
}
</style>
