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
				<input type="date" value={new Date()}>
				<input type="time" value={new Date()}>
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

	{#if selectDateWindow}
		<!-- svelte-ignore a11y-click-events-have-key-events -->
		<div class="datepicker" 
			 on:click={getResult} >
			<Datepicker
				lang="ru"
				bind:selected
				bind:pickerDone
				reSelected/>
		</div>
	{/if}

	{#if selectTimeWindow}
		<div class="timepicker" >
			<TimePicker 
				{options}
				on:change={onChangeTime}
				on:cancel={closeTimeWindow}
  				on:ok={closeTimeWindow} />
		</div>
	{/if}

</div> 

<script>
// @ts-nocheck


import { TimePicker } from 'svelte-time-picker'
import Datepicker from "praecox-datepicker";

let selected = new Date();

let hour = new Date().getHours();
let min = new Date().getMinutes();

let webApp = window.Telegram.WebApp;

	let tgUserInfo = webApp.initDataUnsafe.user;

	let user = {
		name: `${tgUserInfo.first_name} ${tgUserInfo.last_name}`,
		login: tgUserInfo.username
	}


let options = {
	bgColor: '#000000',
    hasButtons: true, 
	is24h: true,
	minutesIncrement: 10,
	buttonCancel: "<p> Отменить </p>",
	buttonNow: "<p> Сброс </p>",
	buttonOK: "<p> ОК </p>",
}

let pickerDone = false;

let selectDateWindow = false;
let selectTimeWindow = false;

function openSelectDateWindow(){
	selectDateWindow = !selectDateWindow;
}

function closeTimeWindow(){
	selectTimeWindow = false;
}

function openSelectTimeWindow(){
	selectTimeWindow = !selectTimeWindow;
}

function formatDate( v ) {

    let date = new Date(v);
    let year = date.getFullYear();
    let month = date.getMonth() + 1;
    let day = date.getDate();

    return `${day}/${month}/${year}`;

}

function onChangeTime( event ){

    hour = new Date( event.detail ).getHours();
	min = new Date( event.detail ).getMinutes();

}

function getResult() {

    if ( pickerDone ) {
		selectDateWindow = false;
    }

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