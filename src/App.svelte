<script lang="ts">

	import { Router, Link, Route } from "svelte-routing";
	import About from "./routes/About.svelte";
	import Portfolio from "./routes/Portfolio.svelte";
	export let url = "";

	import "tw-elements";
    import { onMount } from "svelte";

	let selectedRoute = "person";

	onMount(async () => {

	});

	let webApp = window.Telegram.WebApp;

	let tgUserInfo = webApp.initDataUnsafe.user;

	let user = {
		name: `${tgUserInfo.first_name} ${tgUserInfo.last_name}`,
		login: tgUserInfo.username
	}

	let backButton = webApp.BackButton;
	backButton.isVisible = true;

	let mainButton = webApp.MainButton;
	mainButton.text = "Заказать съёмку";
	mainButton.isVisible = true;
	mainButton.color = "#e8e8e8";
	mainButton.textColor = "#000000";
	mainButton.onClick( openWritingWindow );

	webApp.setHeaderColor(webApp.themeParams.bg_color)

	function openWritingWindow(){

		changeRoute( "writing" );

	}

	function openSuccessDialog(){

		window.Telegram.WebApp.showAlert(
			"Вы записаны на самую лучшую фотосессию в вашей жизни!"
		);

		window.Telegram.WebApp.MainButton.text = "ЗаписатьсяAAA";

	}

	function changeRoute( route ){

		selectedRoute = route;

		if ( route == "writing" ){
			window.Telegram.WebApp.MainButton.onClick( openSuccessDialog ); 
		}

	}

	function handleClick(e) {

		console.log(e)

	}

</script>

<Router url="{url}">
	<div class="header">
		<Link to="/about">
			<button class="btn-small">
				Обо мне
			</button>
		</Link>
		
		<Link to="/portfolio">
			<button class="btn-small">
				Портфолио
			</button>
		</Link>
	
	</div>
	<div>
	  	<Route path="portfolio" component="{Portfolio}" />
	  	<Route path="about" component="{About}" />
	</div>
</Router>

<style lang="scss">

@import "./css/paper/paper.min.css";

.header{
	position: absolute;
	top: 5px; 
	left: 0px;
	width: 100%;
	display: flex;
	justify-content: center;
}

button{
	margin: 5px;
}

a {
	background-image: none !important;
	background-color: red !important;
}

</style>
