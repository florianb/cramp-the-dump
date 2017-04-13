<template lang="html">
	<div class="">
		<h1>Test me, you little crazy</h1>
		<div v-for="logContent in logContents">
			<dump :content="logContent"></dump>
		</div>
	</div>
</template>

<script>
export default {
	components: {
		'dump': require('./dump.vue')
	},
	props: ['logContents']
}
</script>

<style lang="css">
</style>
