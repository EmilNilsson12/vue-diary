<template>
	<div>
		Inside
		<div>Diary entries!</div>
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
