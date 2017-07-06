<template>
	<div>
		<nav class="navbar navbar-default navbar-fixed-top">
			<div class="container">
				<div class="navbar-header">
					<button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#navbar" aria-expanded="false" aria-controls="navbar">
						<span class="sr-only">Toggle navigation</span>
						<span class="icon-bar"></span>
						<span class="icon-bar"></span>
						<span class="icon-bar"></span>
					</button>
					<!--<a class="navbar-brand" href="#">Vue Test</a>-->
					<router-link class="navbar-brand" to="/">Vue Test</router-link>
				</div>
				<div id="navbar" class="navbar-collapse collapse">
					<ul class="nav navbar-nav">
						<li><router-link to="/">Home</router-link></li>
						<li><router-link to="/sobre">Ajuda</router-link></li>
					</ul>
					<ul class="nav navbar-nav navbar-right">
						<li><router-link to="/novo">Novo Usuário</router-link></li>
					</ul>
				</div>
				<!--/.nav-collapse -->
			</div>
		</nav>
		<!--<img src="../assets/logo.png" width="110px" height="110px">-->
		<!--<h1 class="page-header" v-html="message"></h1>-->
	</div>
</template>
<script>
export default {
	props: { message: { type: String, default: 'Gerenciamento de usuários' } }
}
</script>
<style scoped>

</style>