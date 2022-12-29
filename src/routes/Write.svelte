<div class="main">

	<button on:click={openSelectDateWindow}> 
		{selected} 
	</button>

	<button on:click={openSelectTimeWindow}> 
		{time} 
	</button>

	{#if selectDateWindow}
	<div class="datepicker" on:click={getResult}>
		<Datepicker lang="ru" bind:selected bind:pickerDone reSelected/>
	</div>
	{/if}

	{#if selectTimeWindow}
	<div class="timepicker" >
		<TimePicker 
			date={time} 
			{options}
			on:cancel={closeTimeWindow}
  			on:ok={closeTimeWindow} />
	</div>
	{/if}

</div> 

<script>

import { TimePicker } from 'svelte-time-picker'
import Datepicker from "praecox-datepicker";

let selected = new Date();

let time = new Date(2020, 4, 15, 10, 13) // 10:13 AM

let options = {
    bgColor: '#2e2e2e',
    hasButtons: true, 
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

function getResult() {
    if (pickerDone) {
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
	border: 5px solid grey !important;
	border-radius: 10px;
	font-family: "Patrick Hand SC";
}

.main{
	display: flex;
	justify-content: center;
}

#appt{
	height: 40px;
	margin: 5px;
}

button{
	margin: 5px;
	height: 40px;
	font-size: 10px;
}

</style>