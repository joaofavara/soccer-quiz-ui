<template>
	<div>
		<h1>QuestionsForm</h1>
		<md-switch v-model="location" class="md-primary">
			<span v-if="location">Futebol Brasileiro</span>
			<span v-else>Futebol International</span>
		</md-switch>

		<div class="md-layout-item">
			<md-field>
				<md-select v-model="nationalChampionship" placeholder="national Championship">
					<div v-for="(item, index) in nationalOptions" :key="index">
						<md-option :value="item.value">{{ item.label }}</md-option>
					</div>
				</md-select>
			</md-field>
		</div>

		<md-field>
			<label>Pergunta</label>
			<md-textarea v-model="question" md-autogrow></md-textarea>
		</md-field>

		<md-field>
			<label>Opção A</label>
			<md-input v-model="answers.a"></md-input>
		</md-field>
		<md-field>
			<label>Opção B</label>
			<md-input v-model="answers.b"></md-input>
		</md-field>
		<md-field>
			<label>Opção C</label>
			<md-input v-model="answers.c"></md-input>
		</md-field>
		<md-field>
			<label>Opção D</label>
			<md-input v-model="answers.d"></md-input>
		</md-field>

		
		<div class="md-layout-item">
			<md-field>
				<md-select v-model="correctAnswer" placeholder="Alternativa Correta">
					<div v-for="(item, index) in answersOptions" :key="index">
						<md-option :value="item.value">{{ item.label }}</md-option>
					</div>
				</md-select>
			</md-field>
		</div>

		<md-button v-on:click="sendForm" class="md-raised md-primary">Enviar Pergunta</md-button>
	</div>
</template>

<script>
	import MixinForm from './mixins/mixinForm';

	export default {
		name: 'QuestionsForm',
		mixins: [
			MixinForm
		],
		data() {
			return {
				location: false,
				question: '',
				answers: {
					a: null,
					b: null,
					c: null,
					d: null,
				},
				answersOptions: [
					{ value: 'a', label: 'A'},
					{ value: 'b', label: 'B'},
					{ value: 'c', label: 'C'},
					{ value: 'd', label: 'D'}
				],
				correctAnswer: null,
				nationalChampionship: null,
			}
		},
		methods: {
			sendForm() {
				const pergunta = {
					type: this.location ? "Futebol Brasileiro" : "Futebol International",
					championship: this.nationalChampionship,
					question: this.question,
					answers: this.answers,
					correctAnswer: this.correctAnswer
				}

				console.log(pergunta);
			}
		}
	}
</script>

<style>

</style>