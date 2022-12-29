<div class="main">

	<button on:click={openSelectDateWindow}> 
		{selected} 
	</button>

	{#if selectDateWindow}
	<div class="datepicker" on:click={getResult}>
		<Datepicker lang="ru" bind:selected bind:pickerDone reSelected/>
	</div>
	{/if}

	<TimePicker bind:time />
	

</div> 

<script>

import TimePicker  from "svelte-touch-timepicker";
import Datepicker from "praecox-datepicker";

let selected = new Date();

let time = new Date();

$: _time = time.toLocaleTimeString("en-US");

let pickerDone = false;

let selectDateWindow = false

function openSelectDateWindow(){
	selectDateWindow = !selectDateWindow;
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




	--svtt-popup-bg-color: #232323;
    --svtt-popup-color: rgb(255, 255, 255);
    --svtt-popup-radius: 3px;
    --svtt-font-size: 20px;
    --svtt-button-color: white;
    --svtt-button-bg-color: transparent;
    --svtt-border: 1px solid #ffffff;
    --svtt-button-box-shadow: none;
    --svtt-bar-color: #232323;
}

li{
	background-color: #12bc00 !important;
}

.datepicker{
	position: absolute;
    top: 50%;  /* position the top  edge of the element at the middle of the parent */
    left: 50%; /* position the left edge of the element at the middle of the parent */
    transform: translate(-50%, -50%);
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