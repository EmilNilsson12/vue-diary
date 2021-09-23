<template>
	<div>
		This is the Preview
		<h2>
			{{ title }}
		</h2>
		<p>
			{{ body }}
		</p>
		<h4>
			{{ date }}
		</h4>
	</div>
</template>

<script>
export default {
	props: {
		title: String,
		body: String,
		date: String,
	},
};
</script>

<style></style>
