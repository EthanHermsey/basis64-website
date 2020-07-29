<template>
  <div id="app">
		<menubar v-on:scroll="scrollTo" :itemData="itemData"/>

		<div id="container">

			<itemcontainer v-on:show="showCard" v-for="(data, index) in itemData" :key="index" :item="data" :itemIndex="index" ref="items"/>

		</div>

		<itemcard v-show="cardIsShown" v-on:hide="hideCard" :cardData="cardData"/>

  </div>
</template>

<script>

import menubar from './components/menubar.vue';
import itemcontainer from './components/itemcontainer.vue';
import itemcard from './components/itemcard.vue';

export default {
	name: 'App',
	components: {
		menubar,
		itemcontainer,
		itemcard
	},
	data: function () {

		return {
			itemData: Array,

			cardIsShown: false,
			cardData: {

				title: '',
				image: '',
				description: '',
				link: '',
				video: ''

			}
		};

	},
	methods: {
		showCard( data ) {

			let { itemIndex, childIndex } = data;

			this.cardData.title = this.itemData[ itemIndex ].children[ childIndex ].title;
			this.cardData.image = this.itemData[ itemIndex ].children[ childIndex ].img;
			this.cardData.description = this.itemData[ itemIndex ].children[ childIndex ].description;
			this.cardData.link = this.itemData[ itemIndex ].children[ childIndex ].link;
			this.cardData.video = this.itemData[ itemIndex ].children[ childIndex ].video || '';

			this.cardIsShown = true;

		},
		hideCard() {

			this.cardIsShown = false;

		},
		scrollTo( index ) {

			this.$refs.items[ index ].$el.scrollIntoView( { behavior: "smooth", block: "center" } );

		}
	},
	mounted() {

		fetch( '../resources/items.json' )
			.then( response => response.json() )
			.then( data => {

				this.itemData = data;

			} );

	}
};

</script>

<style>

	@import url('https://fonts.googleapis.com/css2?family=News+Cycle&display=swap');

	@font-face {
		font-family: 'EunomiaLight';
		src: url(./assets/eunomia.ttf);
	}

	:root {

		--main-bg-color: rgb(40, 40, 40);
		--sec-bg-color: rgb(60, 60, 60);
		--button-bg-color: #339989;

		--line-color: rgb( 242, 244, 243 );
		--sec-line-color: rgb(180, 180, 180);

		--main-border-color: rgb(100, 100, 100);
		--sec-border-color: rgb(120, 120, 120);

		--scrollbar-thumb-color: rgb(120, 120, 120);
		--scrollbar-thumb-color-hover: rgb(140, 140, 140);

	}

	*::-webkit-scrollbar{
		width:10px;
		background: var(--sec-bg-color);
	}
	*::-webkit-scrollbar-thumb{
		background: var(--button-bg-color);
	}
	*::-webkit-scrollbar-thumb:hover{
		background: var(--scrollbar-thumb-color-hover);
	}

	html, body{

		padding: 0 !important;
		margin: 0 !important;
		width: 100vw;
		height: 100vh;

		overflow-x: hidden;
		user-select: none;

	}

	#app {

		background-color: var(--main-bg-color);
		color: var(--line-color);

		font-family: 'News Cycle';
	}

	#container{
		width: calc( 80vw - (15px * 3) );
		margin-left: 15vw;
		padding-top: 15px;

		display: grid;
		grid-template-columns: repeat(4, 25%);
		row-gap: 15px;
		column-gap: 15px;
	}


	@media only screen and (max-width: 999px) {

		#container{

			margin-left: 5vw;
			padding-top: 65px;
			padding-bottom: 5vh;

			width: calc(90vw - (2 * 15px));


			grid-template-columns: repeat(3, 33.33%);

		}

	}

	@media only screen and (max-width: 750px) {

		#container{

			margin-left: 5%;
			width: calc(90% - 5px);
			grid-template-columns: repeat(2, 50%);
			row-gap: 15px;
			column-gap: 15px;

		}

	}
</style>
