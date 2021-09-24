<template>
	<div>
		<div
			v-for="entry in entries"
			:key="entry.diaryTitle"
			class="diary-entry-format real-entry"
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

<style>
.real-entry {
	border-bottom: 1px solid black;
	text-align: left;
}
.real-entry:last-child {
	border-bottom: none;
}
.diary-entry-format p {
	margin-left: 30px;
}
.diary-entry-format h2 span {
	font-size: 11px;
}
</style>
