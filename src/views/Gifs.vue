<template>
	<div class="container mt-3 border">
		<h1 class="text-center">Gifs</h1>
		<Search @accion="getGifs"/>
		<hr>
		<Loading v-if="load"/>
		<div class="row">
			<div class="col-12 col-lg-3" v-for="gif in gifs" :key="gif.id">
				<GifCard :data="gif" class="m-2 w-75"/>
			</div>
		</div>
	</div>
</template>

<script>
	import GifCard from '../components/GifCard'
	import Search from '../components/Search'
	import Loading from '../components/Loading'
export default {
	components:{
		GifCard,
		Search,
		Loading,
	},
	data: ()=>({
		gifs: {},
		load: false,
	}),
	created(){
		this.getGifs();
	},
	methods:{
		async getGifs(search){
			const key = "HAdjDsHMuZqkvFUf4FtWlpxFZbDQtL7c";

			this.load = true;

			const {data} = await this.axios.get(`https://api.giphy.com/v1/gifs/search?q=${search}&api_key=${key}`)

			//console.log(data);
			this.gifs = data.data;

			this.load = false;
			//console.log(data)
		}
	}
}
</script>
