<template>
	<div class="container">
		<div class="films">
			<div v-for="film in films" class="film_item">
				<img v-bind:src="film.avatar" alt="" /><br/>
				<p>{{ film.titulo }}</p>
			</div>
		</div>
	</div>
</template>

<script>
import axios from "axios";

export default {
	data() {
		return {
			films: []
		}
	},
  mounted() {
	  axios
	  	.get('https://api.b7web.com.br/cinema/')
	  	.then(json => {
		  	this.films = json.data;
	  	});
  }
}
</script>

<style>
	.container {
  		
	}
	.film_item {
		border: 1px solid #ccc;
		padding: 10px;
		margin: 10px;
		max-width: 15%;
	}
	.film_item img {
		width: 100%;
	}	
	.film_item p {
		font-size: 12px;
	}
	.films {
		display: flex;
		flex-wrap: wrap;
		justify-content: space-evenly;
	}
</style>