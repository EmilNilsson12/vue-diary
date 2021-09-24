<template>
	<div class="diary-entry-format preview">
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
.preview {
	border: 2px dashed black;
	text-align: left;
	padding-left: 20px;
}
</style>
