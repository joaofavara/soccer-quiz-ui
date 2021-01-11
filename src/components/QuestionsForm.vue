<template>
	<div>
		<h1>QuestionsForm</h1>
		<md-switch v-model="boolean" class="md-primary">
			<span v-if="boolean">Futebol Nacional</span>
			<span v-else>Futebol Internacional</span>
		</md-switch>
	</div>
</template>

<script>
	export default {
		name: 'QuestionsForm',
		data() {
			return {
				// array: [],
				boolean: false,
				// string: null,
				// novalue: null,
				// disabled: true
			}
		},
	}
</script>

<style>

</style>