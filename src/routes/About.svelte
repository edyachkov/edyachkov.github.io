<div class="name-area">
	<p class="name"> Eduard Ph </p>
</div>

<img src="ed.png">


<script>

let webApp = window.Telegram.WebApp;

let mainButton = webApp.MainButton;
	mainButton.text = "Поставить лайк!";
	mainButton.isVisible = true;
	mainButton.color = "#e8e8e8";
	mainButton.textColor = "#000000";

</script>

<style lang="scss">

	.name-area{
		height: calc(100vh - 115px);
		display: flex;
		justify-content: center;
		align-items: center;
	}

	img[src="ed.png"]{
		border: 0px;
		bottom: 0px;
		left: 0px;
	}

</style>