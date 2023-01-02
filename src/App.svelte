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
		<Link to="/write">
			<button class="btn-small">
				Записаться
			</button>
		</Link>
		
	</div>
	<div>
	  	<Route path="portfolio" component="{Portfolio}" />
	  	<Route path="about" component="{About}" />
		<Route path="write" component="{Write}" />
	</div>
</Router>

<script lang="ts">

	import { Router, Link, Route } from "svelte-routing";
	import About from "./routes/About.svelte";
	import Portfolio from "./routes/Portfolio.svelte";
	import Write from "./routes/Write.svelte";
	export let url = "";
	
	import "tw-elements";
    import { onMount } from "svelte";
  
	let selectedRoute = "person";

	onMount(async () => {

	});

	let webApp = window.Telegram.WebApp;
	webApp.isClosingConfirmationEnabled = true;

	let tgUserInfo = webApp.initDataUnsafe.user;

	let user = {
		name: `${tgUserInfo.first_name} ${tgUserInfo.last_name}`,
		login: tgUserInfo.username
	}

	let backButton = webApp.BackButton;
	backButton.isVisible = true;

	

	webApp.setHeaderColor(webApp.themeParams.bg_color)


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

<style lang="scss">

@import "./css/paper/paper.min.css";

.header{
	position: fixed;
	left: 0px;
	top: 0px;
	width: 100%;
	display: flex;
	justify-content: center;
	z-index: 100;
	// background-color: rgb(23, 23, 23);
	// box-shadow: 5px 20px 10px rgb(23, 23, 23);
}

button{
	margin: 10px;
	height: 40px;
	font-size: 10px;
	background-color: #232323;
	box-shadow: 0px 0px 25px rgb(0, 0, 0);
}

a {
	background-image: none !important;
	background-color: red !important;
}

</style>
