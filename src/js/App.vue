<script>
export default {
	data() {
		return {
			msg:"Olá, Mundo!"
		}
	}
}
</script>

<template>
	<div id="app">
		<h3>{{ msg }}</h3>
		<hr/>

		<router-link to="/">Home</router-link>
		<router-link to="/sobre">Sobre</router-link>
		<router-link to="/contato">Contato</router-link>
		<router-link to="/bitcoin">Preço do Bitcoin</router-link>

		<hr/>

		<router-view></router-view>
	</div>
</template>

<style>
	h3 {
		background-color: #ff0000;
		color: #fff;
		padding: 10px;
	}
	body {
		font-family: arial;
	}
</style>