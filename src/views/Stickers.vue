<template>
	<div class="container mt-3 border">
		<h1 class="text-center">Stickers</h1>
		<Search @accion="getStickers"/>
		<hr>
		<Loading v-if="load"/>
		<div class="row">
			<div class="col-12 col-lg-3" v-for="sticker in stickers" :key="sticker.id">
				<StickerCard :data="sticker" class="m-2 w-75"/>
			</div>
		</div>
	</div>
</template>

<script>
	import StickerCard from '../components/StickerCard'
	import Search from '../components/Search'
	import Loading from '../components/Loading'
export default {
	components:{
		StickerCard,
		Search,
		Loading,
	},
	data: ()=>({
		stickers: {},
		load: false,
	}),
	created(){
		this.getStickers();
	},
	methods:{
		async getStickers(search){
			const key = "HAdjDsHMuZqkvFUf4FtWlpxFZbDQtL7c";

			this.load = true;

			const {data} = await this.axios.get(`https://api.giphy.com/v1/stickers/search?q=${search}&api_key=${key}`)

			//console.log(data);
			this.stickers = data.data;

			this.load = false;
			//console.log(data)
		}
	}
}
</script>
