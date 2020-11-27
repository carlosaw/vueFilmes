<template>
	<div>
		<h2>Bitcoin</h2><br/>
		
		Preço atual do Bitcoin:

		<div v-if="loading">Carregando...</div>
		<div v-else>
			<div v-if="error">Desculpe, não podemos pegar a informação no momento. Tente novamente mais tarde</div>
			<div v-else>US$: {{ bitcoin_price }}</div>
		</div>
	</div>
</template>

<script>
import axios from 'axios';

export default {
	data() {
		return {
            bitcoin_price:0,
			error:false,
			loading:true
		}
	},
	mounted() {
        axios
            .get('https://api.coindesk.com/v1/bpi/currentprice.json')
            .then(r => {

                this.bitcoin_price = r.data.bpi.USD.rate_float;

            })
			.catch(error => {
				this.error = true;
			})
			.finally(()=>{
				this.loading = false;
			});
	}
}
</script>

<style>
	h2 {
		color: #0000FF;
	}
</style>