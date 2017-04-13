<template lang="html">
	<div>
		<input
			type="file"
			accept=".log"
			multiple="true"
			@change="onFileChange"/>
	</div>
</template>

<script>
export default {
	methods: {
		onFileChange(e) {
			const fileList = e.target.files
			const files = []

			for (let i = 0; i < fileList.length; i++) {
				files.push(fileList.item(i))
			}

			Promise.all(
				files.map(file => {
					return new Promise((resolve, reject) => {
						const fileReader = new FileReader()
						fileReader.onabort = err => reject(err)
						fileReader.onerror = err => reject(err)
						fileReader.onloadend = () => resolve(fileReader.result)

						fileReader.readAsText(file)
					})
				})
			)
			.then(contents => {
				console.dir(this)
				this.$emit('setLogContents', contents)
				this.$root.$emit('setLogContents', contents)
			})
		}
	}
}
</script>

<style lang="css">
</style>
