<template>
	<div id="app">
		<dumpImporter></dumpImporter>
		<dumpCramper :log-contents="logContents"></dumpCramper>
		<footer>Containing {{ logContents.length }} content strings.</footer>
	</div>
</template>

<script>
const dumpImporter = require('./dump-importer.vue');
const dumpCramper = require('./dump-cramper.vue');

export default {
	name: 'app',
	data() {
		return {
			logContents: []
		}
	},
	components: {
		dumpImporter,
		dumpCramper
	},
	mounted() {
		this.$root.$on('setLogContents', (contents) => {
			this.logContents = contents
			console.log('set', contents.length, 'log contents')
		})
		console.dir(this)
		console.log('mounted')
	}
}
</script>

<style>
#app {
	font-family: 'Avenir', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}

h1, h2 {
	font-weight: normal;
}

ul {
	list-style-type: none;
	padding: 0;
}

li {
	display: inline-block;
	margin: 0 10px;
}

a {
	color: #42b983;
}
</style>
