<template>
	<div class="add container">
		<Alert v-if="alert" v-bind:message="alert"></Alert>
		<h1 class="page-header">Novo Usuário</h1>
		<form method="post" v-on:submit="addUsuario">
			<div class="well">
				<h4>Detalhes do usuário</h4>
				<div class="form-group">
					<label>Nome</label>
					<input type="text" class="form-control" placeholder="Nome do usuário" v-model="usuario.nome">
				</div>
			</div>
			<button type="submit" class="btn btn-primary" name="button">Enviar</button>
		</form>
	</div>
</template>

<script>

import axios from 'axios';
import Alert from '../components/Alert.vue'

export default {
	name: 'FrmCadastroUsuario',
	data: () => ({
		usuario: {},
		errors: [],
		alert: ''
	}),
	methods: {
		addUsuario(e) {
			if (!this.usuario.nome) {
				this.aler = 'Campo nome Obrigatório';
			} else {

				let novoUsuario = {
					nome: this.usuario.nome
				}

				axios.post('http://localhost:3000/api/usuarios/', novoUsuario)
					.then(response => {
						 this.$router.push({path: '/', query: {alert: 'Usuário cadastrado com sucesso'}});
					})
					.catch(e => {
						this.errors.push(e)
					})
				e.preventDefault();
			}
			e.preventDefault();
		}
	},
	components: {
		Alert
	}
}
</script>
<style scoped>

</style>