<template>
	<div class="diary-entry-format">
		<h2>
			{{ title }}
			<span>{{ date }}</span>
		</h2>
		<p>
			{{ body }}
		</p>
	</div>
</template>

<script>
export default {
	name: 'Preview',
	props: {
		title: String,
		body: String,
		date: String,
	},
};
</script>

<style>
.diary-entry-format {
	text-align: left;
}
.diary-entry-format p {
	margin-left: 30px;
}
.diary-entry-format h2 span {
	font-size: 11px;
}
</style>
