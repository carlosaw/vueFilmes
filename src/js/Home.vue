<template>
		
	<div class="container">
					
		<div v-if="error">Desculpe, não podemos pegar as informações no momento. Tente novamente mais tarde!</div>
		<div v-else class="cartaz"><h2>Filmes em Cartaz</h2></div>
						
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
			films: [],
			error:false,
			loading:true
		}
	},
  mounted() {
	  axios
	  	.get('https://api.b7web.com.br/cinema/')
	  	.then(json => {
		  	this.films = json.data;
	  	})
		.catch(error => {
			this.error = true;
		})
  }
}
</script>

<style>
	.container {
  		display: flex;
		  flex-direction: column;
	}
	.film_item {
		border: 1px solid #EEE);
		padding: 10px;
		margin: 0px;
		max-width: 15%;
	}
	.film_item img {
		width: 100%;
	}	
	.film_item p {
		font-size: 12px;
		text-align: center;
		margin-top: 0px 0px -15px -3px;
	}
	.films {
		display: flex;
		flex-wrap: wrap;
		justify-content: space-evenly;
	}
	.cartaz h2 {
		text-align: center;
	}
</style>