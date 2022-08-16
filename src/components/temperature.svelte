<script>
	// Fahrenheit is C = (F - 32) * (5/9) and the dual direction is F = C * (9/5) + 32.
	let fahrenheit = 0;
	let celsius = 0;

	const isNumber = (value) => {
		return !isNaN(parseFloat(value)) && isFinite(value);
	};

	const handleChange = ({ target: { value } }, callback) => {
		if (isNumber(value)) {
			callback(value);
		}
	};

	const handleFahrenheitChange = (event) => {
		handleChange(event, (value) => {
			fahrenheit = value;
			celsius = (fahrenheit - 32) * (5 / 9);
		});
	};

	const handleCelsiusChange = (event) => {
		handleChange(event, (value) => {
			celsius = value;
			fahrenheit = celsius * (9 / 5) + 32;
		});
	};
</script>

<h2>Temperature</h2>
<label for="fahrenheit"
	>fahrenheit
	<input type="text" id="fahrenheit" bind:value={fahrenheit} on:input={handleFahrenheitChange} />
</label>
<label for="celcius"
	>celcius
	<input type="text" id="celcius" bind:value={celsius} on:input={handleCelsiusChange} />
</label>
