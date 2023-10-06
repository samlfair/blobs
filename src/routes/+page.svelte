<script>	
	let blob = 1;
  
	/**
   * @type {number}
   */
	let rearGradient
	/**
   * @type {number}
   */
	let foreGradient
	/**
   * @type {number}
   */
	let noise

	/**
   * @param {number} num
   */
	function randomNumber(num) {
		return Math.floor(Math.random() * num) + 1
	}

	function setGradients() {
		rearGradient = randomNumber(20)
		foreGradient= randomNumber(20)
		noise = randomNumber(5)
	}

	setGradients()

	setInterval(() =>{
		blob = randomNumber(5)
	}, 1000)
</script>

<main 
	style:background-image="var(--gradient-{rearGradient})"
	style:filter="var(--noise-filter-{noise})"
  on:click={setGradients}
>
	<div 
		class="blob" 
		style:border-radius="var(--radius-blob-{blob})" 
		style:background-image="var(--gradient-{foreGradient})"
		style:--noise={noise}
	/>
</main>

<style global>
	/* the props */
  @import "open-props/style";

  /* optional imports that use the props */
  @import "open-props/normalize";
  @import "open-props/buttons";

	main {
		display: grid;
		height: 100vh;
		background-image: var(--gradient-10);
	}

	div {
		grid-row: 1/2;
		grid-column: 1/2;
	}

	.blob {
		background-image: var(--gradient-18);
		aspect-ratio: 1;
		margin: auto;
		height: 300px;
		filter: blur(50px);
		transition: border-radius 5s;
	}
</style>