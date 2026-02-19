<svelte:head>
  <title>Contact me</title>
</svelte:head>

<nav>
    <a href=".">Home</a>
    <a href="projects">Projects</a>
    <a href="contact" class="current">Contact</a>
    <a href="resume">Resume</a>
    <a href="https://github.com/yoyo-yuan" target="_blank">GitHub</a>
</nav>
<h1>Contact</h1>
<form action="mailto:96553765+yoyo-yuan@users.noreply.github.com" method="get">
	<label>
	Email: <input name="email" type="email" value="test@gmail.com"/>
	</label>
	<label>
	Subject: <input name="subject" value="test"/>
	</label>
	<label>
	Body: <textarea name="body" value="test"></textarea>
	</label>
	<button>Send</button>
</form>
