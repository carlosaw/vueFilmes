<template>
	<div>
		<h2>Bitcoin</h2><br/>
		
		Preço atual do Bitcoin:

        <div>US$: {{ bitcoin_price }}</div>
	</div>
</template>

<script>
import axios from 'axios';

export default {
	data() {
		return {
            bitcoin_price:0
		}
	},
	mounted() {
        axios
            .get('https://api.coindesk.com/v1/bpi/currentprice.json')
            .then(r => {

                this.bitcoin_price = r.data.bpi.USD.rate_float;

            });
	}
}
</script>

<style>
	h2 {
		color: #0000FF;
	}
</style>