<script lang="ts">
	
	import "tw-elements";
	import { DateInput } from "date-picker-svelte";

	import Gallery from 'svelte-image-gallery';
    import { onMount } from "svelte";

	let date = new Date();

	let modalWindow = false; // модальное окно записи

	let selectedRoute = "person";

	let tgUserInfo = window.Telegram.WebApp.initDataUnsafe.user

	let user = {
		name: `${tgUserInfo.first_name} ${tgUserInfo.last_name}`,
		login: tgUserInfo.username
	}

	window.Telegram.WebApp.MainButton.text = "Заказать съёмку";
	window.Telegram.WebApp.MainButton.isVisible = true;
	window.Telegram.WebApp.MainButton.color = "#e8e8e8";
	window.Telegram.WebApp.MainButton.textColor = "#000000";
	window.Telegram.WebApp.MainButton.onClick( openWritingWindow );

	window.Telegram.WebApp.setBackgroundColor("#ffffff")

	onMount(async () => {
		

	});


	function openWritingWindow(){

		changeRoute( "writing" );

	}

	function openSuccessDialog(){

		window.Telegram.WebApp.showAlert(
			"Вы записаны на самую лучшую фотосессию в вашей жизни!"
		);

		window.Telegram.WebApp.MainButton.text = "ЗаписатьсяAAA";


	}

	window.Telegram.WebApp.BackButton.isVisible = true;

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

<!--{ #if false}
	img class="bckg" src="back.png">
{ /if }

{ #if selectedRoute == "person" }
	<img class="bckg" src="person-background.png">
	<div class="right-panel"> 
		<div class="info-text"> 
			Меня зовут Эд и я круто-круто снимаю самые крутые фотки!
		</div> </div>
	<div class="left-panel"> 
		<div class="info-text"> 
			Живу в Островце, но ты можем пофоткаться хоть где!
		</div>
	</div>
{ /if }-->

<!--div class="back">

	<div class="header" style={ selectedRoute == "person" ? "color: black" : "color: gray" }>
		<button 
			class="header-button" 
			on:click={()=>changeRoute("person")}> 
			Обо мне 
		</button>
		<button 
			class="header-button" 
			on:click={()=>changeRoute("portfolio")}> 
			Портфолио 
		</button>
	</div>

	{ #if selectedRoute == "writing" }
	<div 
		class="modal">
		Как тебя зовут, {user.login}?
		<input id="nameInput" class="input" autofocus value={user.name} type="text"/>
	</div>
	<div >
		На какое число тебя записать?
		<DateInput />
	</div>
	{ /if }

	{ #if selectedRoute == "portfolio" }

	<Gallery on:click={handleClick} >
		<img src="ph2.png" />
		<img src="ph3.png" />
		<img src="ph1.png" />
	</Gallery>



	<div class="rounded">
	<div
		id="carouselExampleControls"
		class="carousel slide relative"
		data-bs-ride="carousel">

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
	</div>

	{/if}



</div-->
<div >
<p>Inspired by <a href="https://codepen.io/tmrDevelops/pen/VeRvKX" target="_blank">Imperfect Buttons</a></p>
<button class="btn-large">Large</button>
<button>Default</button>
<button class="btn-small">Small</button>
<a href="#" class="paper-btn">Link</a>
<div class="row">
  <div class="col-6 col">
    <button class="btn-block">Block level</button>
  </div>
</div>
<button class="disabled">Disabled</button>
<button disabled>Disabled</button>
</div>
<style lang="scss">

	/*.header {
		margin: 5px;
		top: 0px;
		left: 0px;
		width: 100%;
	}

	.back {
		top: 0px;
		left: 0px;
		position: absolute;
		height: 100%;
		width: 100%;
		/*background-image:
    	/*linear-gradient(rgb(27, 27, 27) 0%, rgba(255, 255, 255, 0.73) 20%), rgba(255, 255, 255, 0.73) 20%,*/
    	/*url('back.jpg');
    	background-size: cover; 
    	padding: 20px;
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

	.bckg{
		width: 100%; 
		position: absolute;
		top: 0px;
		left: 0px;
	}

	.rounded{
		
		box-shadow: 0px 0px 15px #000000;
		margin-top: 50px;
	}

	.slide{
		width: 100% !important;
	}

	.header-button{
		border-bottom: 1px solid rgb(200, 200, 200);
		box-sizing: content-box;
		margin: 10px;
	}

	.header-button:hover{
		border-bottom: 1px solid rgb(27, 27, 27);
	}

	.right-panel{
		position: absolute;
		top: 250px;
		right: 0px;
		width: 200px;
		height: 100px;
		background-color: #ffffff;
		opacity: 0.5;
		display: flex;
		justify-content: center;
		align-items: center;
		color:rgb(60, 60, 60)0;
		font-size: 12px;
	}

	.left-panel{
		position: absolute;
		bottom: 100px;
		left: 0px;
		width: 150px;
		height: 100px;
		background-color: #ffffff;
		opacity: 0.5;
		display: flex;
		justify-content: center;
		align-items: center;
		color:rgb(0, 0, 0)0;
		font-size: 10px;
	}

	.info-text{
		position: relative;
		color:#000000; 
		font-family: 'Andale Mono', monospace;
		font-weight: bold;
	}


:root {
	--date-input-width: 5000;
}*/
@import url(https://unpkg.com/papercss@1.9.0/dist/paper.min.css);
@import url("https://fonts.googleapis.com/css?family=Material+Icons+Round");

* {
  box-sizing: border-box;
}

:root {
  --gap: 10px;
  --transition: all 0.2s ease-in-out;
  --bgGradient: linear-gradient(
    318.32deg,
    #c3d1e4 0%,
    #1a1a1a 55%,
    #d4e0ed 100%
  );

  --btnSize: 15px;
  --btnBorderRadius: 5px;
  --borderGap: 1px;
  --btnOuterShadow: 4px 2px 16px rgba(66, 66, 66, 0.48),
    -4px -2px 16px #282828;
  --btnCheckedInsetShadow: inset 3px 3px 7px rgba(68, 68, 68, 0.48),
    inset -3px -3px 7px #181818;

  --btnContentBorderRadius: calc(var(--btnBorderRadius) - var(--borderGap));
  --iconColor: rgba(77, 77, 77, 0.8);
  --iconSize: calc((var(--btnSize) / 2));
  --iconShadow: 2px 2px 2px rgba(85, 85, 85, 0.6), 0 0 0 rgb(62, 62, 62),
    2px 2px 2px rgba(214, 225, 239, 0);
  --btnCheckedIconShadow: 1px 1px 1px rgba(26, 26, 26, 0.6), 0 0 0 #000,
    1px 1px 1px rgba(214, 225, 239, 0);
}

html,
body {
  width: 100%;
  height: 100%;
  margin: 0;
}

body {
  background: var(--bgGradient);
  display: grid;
  place-items: center;
}

.btns-wrapper {
  display: grid;
  grid-auto-flow: column;
  padding: var(--gap);
  gap: var(--gap);
  transform: scale(3);
}
.visually-hidden {
  border-width: 0 !important;
  clip: rect(1px, 1px, 1px, 1px) !important;
  height: 1px !important;
  overflow: hidden !important;
  padding: 0 !important;
  position: absolute !important;
  white-space: nowrap !important;
  width: 1px !important;
}

.btn {
  outline: none;
  border: none;
  background: none;
  width: calc(var(--btnSize) * 2);
  height: var(--btnSize);
  position: relative;
  border-radius: var(--btnBorderRadius);
  padding: var(--borderGap);
  box-shadow: var(--btnOuterShadow);
  -webkit-tap-highlight-color: transparent;

  .content-wrapper {
    cursor: pointer;
    width: 100%;
    height: 100%;
    border-radius: var(--btnContentBorderRadius);
    transition: var(--transition);
    display: grid;
    place-items: center;

    i {
      user-select: none;
      transition: var(--transition);
      font-size: var(--iconSize);
      position: relative;
      pointer-events: none;
      color: var(--iconColor);
      text-shadow: var(--iconShadow);
    }
  }
}

input[type="radio"]:checked + label {
  box-shadow: var(--btnCheckedInsetShadow);
  i {
    text-shadow: var(--btnCheckedIconShadow);
  }
}

.btn-cntxt{
  	color: #7c7c7c; 
  	display: flex;
	align-items: center;
	justify-content: space-between;
	//flex-direction: column;
	font-size: 3px;
	line-height: 4px;
}


</style>
