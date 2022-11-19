<script lang="ts">
	import "tw-elements";

	import { DateInput } from "date-picker-svelte";
	let date = new Date();

	let modatWindow = false; // модальное окно записи

	let selectedRoute = "modal";

	let user =
		window.Telegram.WebApp.initDataUnsafe.user.first_name +
		"\n" +
		window.Telegram.WebApp.initDataUnsafe.user.last_name +
		"(" +
		window.Telegram.WebApp.initDataUnsafe.user.username +
		")";

	window.Telegram.WebApp.MainButton.text = "Заказать съёмку";
	window.Telegram.WebApp.MainButton.isVisible = true;
	window.Telegram.WebApp.MainButton.color = "#212121";
	window.Telegram.WebApp.MainButton.onClick(() => {
		modalWindow = true;
	});
	window.Telegram.WebApp.MainButton.text = "ОТМЕНИТЬ СТАНЦИЮ";
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

	<DateInput bind:value={date} />

	{user}

	{ #if selectedRoute == "modal" }
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
		position: absolute;
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
		background-color: rgb(41, 41, 41);
	}

	p {
		animation-duration: 3s;
		animation-name: slidein;
		animation-iteration-count: infinite;
	}

	/* The animation code */
	@keyframes example {
		from {
			height: 100px;
			width: 100px;
		}

		to {
			height: 200px;
			width: 200px;
		}

		77% {
			height: 300px;
			width: 300px;
		}
	}

	/* The element to apply the animation to */
	div {
		/* Specify a name for the @keyframes animation */
		animation-name: example;

		/*  */
		animation: name duration timing-function delay iteration-count direction
			fill-mode play-state;

		/* Specifies a delay for the start of an animation */
		animation-delay: time|initial|inherit; /* default: 1s */

		/* Specifies whether an animation should be played */
		animation-direction: forwards|backwards|alternate; /* default: forwards */

		/* Specifies how long time an animation should take to complete one cycle */
		animation-duration: time|initial|inherit; /* default: 0s */

		/* Specifies a style for the element when the animation is not playing (before it starts, after it ends, or both) */
		animation-fill-mode: none|forwards|backwards|both|initial|inherit;

		/* Specifies the number of times an animation should be played */
		animation-iteration-count: number|infinite|initial|inherit; /* default: 1s */

		/* Specifies the name of the @keyframes animation */
		animation-name: keyframename|none|initial|inherit; /* default: none */

		/* Specifies whether the animation is running or paused */
		animation-play-state: paused|running|initial|inherit; /* default: running */

		/* Specifies the speed curve of the animation */
		animation-timing-function: linear|ease|ease-in|ease-out|
			ease-in-out|step-start| step-end|steps(int, start|end) |
			cubic-bezier(n, n, n, n) |initial|inherit; /* default: linear */
	}
</style>
