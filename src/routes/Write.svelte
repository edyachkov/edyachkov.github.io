<!--div class="back">

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

</div--> 