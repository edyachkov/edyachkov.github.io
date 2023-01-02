<div class="main">

	<div class="form-group">
		<div class="user-input"> 
			<p class="label"> Имя: </p> 
			<input value={user.name} type="text" placeholder="Введите имя"> 
		</div>
		<div class="user-input"> 
			<p class="label">  Telegram: </p> 
			<input value={user.login} type="text" disabled> 
		</div>
		<div class="user-input"> 
			<p class="label"> Время: </p> 
			<div class="is-flex">
				<input type="date" bind:value={selectedDate}>
				<input type="time" bind:value={selectedTime}>
			</div>
		</div>
		
		<label for="paperRadios1" class="paper-radio">
			<input type="radio" name="paperRadios" id="paperRadios1" value="option 1"> 
			<span> Семейная съёмка </span>
		  </label>
		  <label for="paperRadios2" class="paper-radio">
			<input type="radio" name="paperRadios" id="paperRadios2" value="option 2"> 
			<span> Индивидуальная съёмка </span>
		  </label>
		
	</div>

</div> 

<script>
// @ts-nocheck
import { onMount } from "svelte";

let selectedDate = new Date();
let selectedTime = new Date();

onMount(() => {
	selectedDate = new Date();
	selectedTime = new Date();
});


let webApp = window.Telegram.WebApp;

let tgUserInfo = webApp.initDataUnsafe.user;

let user = {
	name: `${tgUserInfo.first_name} ${tgUserInfo.last_name}`,
	login: tgUserInfo.username
}

let mainButton = webApp.MainButton;
	mainButton.text = "Заказать съёмку";
	mainButton.isVisible = true;
	mainButton.color = "#e8e8e8";
	mainButton.textColor = "#000000";
	mainButton.onClick( openWritingWindow );


function openWritingWindow(){

	const requestOptions = {
		method: 'POST',
		headers: { 'Content-Type': 'application/json' },
		body: JSON.stringify({})
	};

	fetch('http://192.168.1.44:3000/book', requestOptions);

}

</script>

<style lang="scss">
 
:root{
--praecox-calendar-custom-width: 330px;
--praecox-calendar-custom-height: 310px;
--praecox-calendar-custom-inner-width: 310px;
--praecox-calendar-custom-inner-height: 220px;
--praecox-calendar-custom-head-height: 48px;
--praecox-calendar-custom-icon-size: 20px;
--praecox-calendar-custom-border-radius: 3px;
--praecox-calendar-custom-font-family: "Patrick Hand SC";
--praecox-calendar-custom-number-font-family: "Patrick Hand SC", "Patrick Hand SC";

--praecox-calendar-custom-main-color: #939393;
--praecox-calendar-custom-main-color-hover: #979797;
--praecox-calendar-custom-main-color-active: #9b9b9b;
--praecox-calendar-custom-focused-color: #12bc00;
--praecox-calendar-custom-adjunctive-color: rgba(255, 255, 255, 0.1);
--praecox-calendar-custom-secondary-color: rgba(86, 86, 86, 0.826);
--praecox-calendar-custom-selected-color: #ffffff;

--praecox-calendar-custom-weekend-color: #2e2e2e;
--praecox-calendar-custom-outsidemonth-color: #000000;
--praecox-calendar-custom-overbackground-color: #f5f8ff;

--praecox-calendar-custom-font-main-color: #ffffff;
--praecox-calendar-custom-font-disabled-color: #d7d7db;
--praecox-calendar-custom-font-secondary-color: #b1b1b3;

--praecox-calendar-custom-background: #232323;
--praecox-calendar-custom-background-hover: #f5f8ff;
--praecox-calendar-custom-border: 1px solid #919191;
--praecox-calendar-custom-boxshadow: 0px 1px solid #ededf0;

}

.datepicker{
	position: absolute;
    top: 50%;  /* position the top  edge of the element at the middle of the parent */
    left: 50%; /* position the left edge of the element at the middle of the parent */
    transform: translate(-50%, -50%);
}

.timepicker{
	position: absolute;
    top: 50%;  /* position the top  edge of the element at the middle of the parent */
    left: 50%; /* position the left edge of the element at the middle of the parent */
    transform: translate(-50%, -50%);
	border: 1px solid grey !important;
	border-radius: 3px;
	font-family: "Patrick Hand SC"; 
	background-color: #2e2e2e;
	color: black;
}

.main{
	display: flex;
	justify-content: center;
	flex-direction: column;
}

#appt{
	height: 40px;
	margin: 5px;
}

button{
	margin: 5px;
	height: 40px;
	font-size: 10px;
	background-color: #232323;
}

.user-input{
	display: flex;
	flex-direction: row;
	align-items: center;
	justify-content: space-between;
	margin: 10px;
}

.label{
	margin: 5px;
	text-align: end;
}

.is-flex{
	width: 100% !important;
	display: flex !important;
	flex-direction: row;
	justify-content: space-between;
}

.form-group{
	width: 100%;
}

input[type="date"]{
	height: 40px;
}

input[type="time"]{
	height: 40px;  
}

span{
	font-family: "Neucha" ,sans-serif !important; 
}

</style>