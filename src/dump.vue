<template lang="html">
	<div class="">
		<pre>{{ content }}</pre>
	</div>
</template>

<script>
export default {
	props: ['content'],
	computed: {
		dumps() {
			const lines = this.content.split(/$/)
			return lines.map(cur => {
				const fields = cur.split('\t', 4)
				return {
					timestamp: fields[0],
					type: fields[2],
					file: fields[3],
					dump: JSON.parse(fields[4])
				}
			})
		}
	}
}
</script>

<style lang="css">
</style>
