<script>
  import projects from "$lib/projects.json";
  import Project from "$lib/Project.svelte";
</script>

<svelte:head>
  <title>Projects</title>
</svelte:head>

<nav>
    <a href=".">Home</a>
    <a href="projects" class="current">Projects</a>
    <a href="contact">Contact</a>
    <a href="resume">Resume</a>
    <a href="https://github.com/yoyo-yuan" target="_blank">GitHub</a>
</nav>
<h1>{ projects.length } Projects</h1>
<div class="projects">
	{#each projects as p}
		<Project data={p} />
	{/each}
	<!-- <article>
		<h2>Nesciunt vel quos quidem?</h2>
		<img src="https://vis-society.github.io/labs/2/images/empty.svg" alt="">
		<p>Esse incidunt consequatur quae harum nulla, quo accusamus laudantium, exercitationem molestiae eaque labore doloribus iste fugit magnam. Inventore ab aliquam expedita quidem maxime veritatis, reprehenderit in. Debitis quod totam laudantium.</p>
	</article>
	<article>
		<h2>Doloremque voluptates veniam sit.</h2>
		<img src="https://vis-society.github.io/labs/2/images/empty.svg" alt="">
		<p>Sed molestias deleniti ea quasi voluptatum ipsa consequatur animi unde, rerum quas tempora, iusto aperiam reprehenderit eveniet voluptates officiis ad. Voluptatibus sint asperiores amet corrupti magni obcaecati maiores soluta quas?</p>
	</article>
	<article>
		<h2>Similique velit voluptatum beatae?</h2>
		<img src="https://vis-society.github.io/labs/2/images/empty.svg" alt="">
		<p>Atque quas, debitis cumque dolores quia ea aspernatur explicabo doloremque nisi id aut saepe earum veniam inventore, distinctio nulla, ipsa veritatis laudantium est nesciunt maxime. Minus eos velit aliquam animi.</p>
	</article>
	<article>
		<h2>Iusto eum earum mollitia!</h2>
		<img src="https://vis-society.github.io/labs/2/images/empty.svg" alt="">
		<p>Reiciendis, eligendi laudantium in sint cumque, laboriosam fugiat error nisi vero qui optio ut asperiores maiores veniam deleniti. Expedita exercitationem tempora cumque consequatur unde molestiae aspernatur architecto enim totam distinctio.</p>
	</article>
	<article>
		<h2>Ex quas neque suscipit!</h2>
		<img src="https://vis-society.github.io/labs/2/images/empty.svg" alt="">
		<p>Reiciendis provident, dolor, odio asperiores ullam ad commodi aperiam nobis, mollitia nam consequatur vel velit impedit officiis quo! Officia delectus eius sed ex nesciunt pariatur ipsum reprehenderit architecto fugit hic.</p>
	</article>
	<article>
		<h2>Voluptatem maxime neque itaque?</h2>
		<img src="https://vis-society.github.io/labs/2/images/empty.svg" alt="">
		<p>Fugit provident cumque aliquid. Architecto sed asperiores iure earum laborum beatae sequi quia a! Nostrum velit numquam laudantium in, rem incidunt quam consequatur hic nobis nesciunt quod quas cumque eveniet!</p>
	</article>
	<article>
		<h2>Praesentium fugit debitis dolor.</h2>
		<img src="https://vis-society.github.io/labs/2/images/empty.svg" alt="">
		<p>Nihil sunt quam quibusdam eveniet? Consequatur, enim! Rerum minus veritatis quos! Quis quos eum eveniet consectetur quod quia quibusdam quasi consequuntur exercitationem, doloremque ad consequatur ab atque eius id libero.</p>
	</article>
	<article>
		<h2>Velit amet repellendus dolor.</h2>
		<img src="https://vis-society.github.io/labs/2/images/empty.svg" alt="">
		<p>Quibusdam consequuntur dolor laboriosam optio ipsa perspiciatis magni atque earum fuga cupiditate. Dignissimos illo eaque magnam corporis consectetur sed cupiditate temporibus ab natus perspiciatis aspernatur placeat esse, quo earum blanditiis!</p>
	</article>
	<article>
		<h2>Aliquid recusandae excepturi fugiat?</h2>
		<img src="https://vis-society.github.io/labs/2/images/empty.svg" alt="">
		<p>Iste, ut. Aliquam eaque architecto odio a, numquam quod sapiente sed eos recusandae animi dolore fugiat placeat aut enim ab inventore? Eligendi aliquam nesciunt, quos suscipit illo rem ipsa. Eum.</p>
	</article>
	<article>
		<h2>Totam numquam ullam beatae.</h2>
		<img src="https://vis-society.github.io/labs/2/images/empty.svg" alt="">
		<p>Esse animi ipsa saepe repellat. Voluptatem, earum consequuntur? Mollitia, quibusdam doloribus eveniet odit tenetur sequi optio sed officiis maxime natus hic, exercitationem, aliquid fugiat? Nisi tenetur ipsum minima harum veniam?</p>
	</article>
	<article>
		<h2>Placeat minus velit repudiandae!</h2>
		<img src="https://vis-society.github.io/labs/2/images/empty.svg" alt="">
		<p>Ad recusandae architecto veritatis temporibus explicabo, officiis, laboriosam quas id eos ea ipsa. Quia, necessitatibus reiciendis magni vero atque optio dicta dolorum totam minus asperiores obcaecati quae ex excepturi dolores!</p>
	</article> -->
</div>
