<script lang="ts">
	import "tw-elements";

	import { DateInput } from "date-picker-svelte";
	let date = new Date();

	let modatWindow = false; // модальное окно записи

	let selectedRoute = "modal";

	let tgUserInfo = window.Telegram.WebApp.initDataUnsafe.user

	let user = {
		name: `${tgUserInfo.first_name} ${tgUserInfo.last_name}`,
		login: tgUserInfo.username
	}

	window.Telegram.WebApp.MainButton.text = "Заказать съёмку";
	window.Telegram.WebApp.MainButton.isVisible = true;
	window.Telegram.WebApp.MainButton.color = "#212121";
	window.Telegram.WebApp.MainButton.onClick(() => {
		modalWindow = true;
	});
	
	window.Telegram.WebApp.showAlert({
		message: "Ghbdtn!",
		title: "dfdfgdfg",
	});
	window.Telegram.WebApp.BackButton.isVisible = true;

</script>

<div class="back">

	<div class="header">
		<button> Обо мне </button>
		<button> Портфолио </button>
		<button> Записаться </button>
	</div>

	<!--DateInput bind:value={date} /-->

	{ #if selectedRoute == "modal" }
	<div 
		class="modal">
		Как тебя зовут, {user.login}?
		<input class="input" value={user.name} type="text"/>
	</div>
	{ /if }

	{ #if selectedRoute != "modal" }
	<div
		id="carouselExampleControls"
		class="carousel slide relative"
		data-bs-ride="carousel"
	>
		<div class="carousel-inner relative w-full overflow-hidden">
			<div class="carousel-item active relative float-left w-full">
				<img src="ph2.png" class="block w-full" alt="Wild Landscape" />
			</div>
			<div class="carousel-item relative float-left w-full">
				<img src="ph3.png" class="block w-full" alt="Camera" />
			</div>
			<div class="carousel-item relative float-left w-full">
				<img src="ph1.png" class="block w-full" alt="Exotic Fruits" />
			</div>
		</div>
		<button
			class="carousel-control-prev absolute top-0 bottom-0 flex items-center justify-center p-0 text-center border-0 hover:outline-none hover:no-underline focus:outline-none focus:no-underline left-0"
			type="button"
			data-bs-target="#carouselExampleControls"
			data-bs-slide="prev"
		>
			<span
				class="carousel-control-prev-icon inline-block bg-no-repeat"
				aria-hidden="true"
			/>
			<span class="visually-hidden">Previous</span>
		</button>
		<button
			class="carousel-control-next absolute top-0 bottom-0 flex items-center justify-center p-0 text-center border-0 hover:outline-none hover:no-underline focus:outline-none focus:no-underline right-0"
			type="button"
			data-bs-target="#carouselExampleControls"
			data-bs-slide="next"
		>
			<span
				class="carousel-control-next-icon inline-block bg-no-repeat"
				aria-hidden="true"
			/>
			<span class="visually-hidden">Next</span>
		</button>
	</div>

	{/if}

</div>

<style>

	.header {
		margin: 5px;
		top: 0px;
		left: 0px;
		width: 100%;
	}
	.logo {
		height: 6em;
		padding: 1.5em;
		will-change: filter;
	}
	.logo:hover {
		filter: drop-shadow(0 0 2em #646cffaa);
	}
	.logo.svelte:hover {
		filter: drop-shadow(0 0 2em #ff3e00aa);
	}
	.read-the-docs {
		color: #888;
	}

	.back {
		top: 0px;
		left: 0px;
		position: absolute;
		height: 100%;
		width: 100%;
		background-color: red;
		/*background: url(back.jpg);*/
		color: black;
	}

	p {
		animation-duration: 3s;
		animation-name: slidein;
		animation-iteration-count: infinite;
	}

	.modal{
		display: flex;
		flex-direction: column;
	}

	input{
		margin: 5px 20% 5px 20%;
		padding: 5px;
		border-radius: 5px;
		text-align: center;
		background: none;
		border: 2px solid black;
	}

</style>
