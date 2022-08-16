<script>
	let journey = '1';
	let from = '';
	let to = '';
	$: isOneWay = journey === '1';

	const regex = new RegExp(/(\d{1,2})\.(\d{1,2})\.(\d{4})/);

	let day = null;
	let month = null;
	let year = null;

	const isBetween = (value, min, max) => {
		if (!value) return false;
		return value >= min && value <= max;
	};

	const setFieldValid = (field, isValid) => {
		if (!isValid) {
			field.setCustomValidity('invalid date');
		} else {
			field.setCustomValidity('');
		}
	};

	const validDate = (year, month, day) => {
    const date = new Date(year, month - 1, day);
  };

	const validate = ({ target }) => {
		const { value } = target;
		const match = value.match(regex);
		if (!match) {
			setFieldValid(target, false);
			return;
		}
		const [, day, month, year] = match;

		const date = validDate(year, month, day);
		if (!match) {
			setFieldValid(target, false);
		} else {
			setFieldValid(
				target,
				isBetween(day, 1, 31) && isBetween(month, 1, 12) && isBetween(year, 1900, 2100)
			);
		}
	};
</script>

<h2>Flight Booker</h2>
<select bind:value={journey}>
	<option value="1">one way flight</option>
	<option value="2">return flight</option>
</select>

<input type="text" bind:value={from} placeholder="from" on:input={validate} />
<input type="text" bind:value={to} placeholder="to" disabled={isOneWay} />

<style>
	input:invalid {
		background-color: red;
		color: white;
	}
</style>
