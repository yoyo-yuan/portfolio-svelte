<script>
	function handleSubmit(event) {
		event.preventDefault();
		let form = event.target;
		let data = new FormData(form);
		let url = form.action + "?";
		for (let [name, value] of data) {
			url += (name + "=" + encodeURIComponent(value) + "&");
		}
		location.href = url;
	}
</script>

<svelte:head>
  <title>Contact me</title>
</svelte:head>

<h1>Contact</h1>
<form action="mailto:96553765+yoyo-yuan@users.noreply.github.com" method="get" on:submit={handleSubmit}>
	<label>
		Subject: <input name="subject" value="test"/>
	</label>
	<label>
		Body: <textarea name="body" value="test"></textarea>
	</label>
	<button>Send</button>
</form>
