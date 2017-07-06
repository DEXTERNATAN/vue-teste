<template>
	<div class="container">
		<router-link to="/">Voltar</router-link>
		<h1 class="page-header">Detalhe Usuário
			<span class="pull-right">
				<router-link class="btn btn-primary" v-bind:to="'/editarUsuario/' + usuario.id">Editar</router-link>
				<button class="btn btn-danger" v-on:click="DeletaUsuario(usuario.id)">Apagar</button>
			</span>
		</h1>
		<ul class="list-group">
			<li class="list-group-item">
				<span class="glyphicon glyphicon-phone" aria-hidden="true"></span> {{usuario.nome}}</li>
			<li class="list-group-item">
				<span class="glyphicon glyphicon-envelope" aria-hidden="true"></span> {{usuario.nome}}</li>
		</ul>
	</div>
</template>

<script>

import axios from 'axios';
export default {
	name: 'detalheUsuario',
	data: () => ({	
			usuario: '',
			errors: []
	}),
	methods: {
		BuscaUsuario(id) {
			axios.get('http://localhost:3000/api/usuarios/' + id)
				.then(response => {
					this.usuario = response.data;
				})
				.catch(e => {
					this.errors.push(e)
				})
		},
		DeletaUsuario() {
			axios.delete('http://localhost:3000/api/usuarios/' + this.$route.params.id).then(response => {
				console.log(response.data);
				this.$router.push({ path: '/', query: {alert: 'Usuário excluído com sucesso!'} });
			});
		},
	},
	created() {
		this.BuscaUsuario(this.$route.params.id);
	}

}
</script>
<style scoped>
</style>