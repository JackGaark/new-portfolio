<script>
	/*
	 * Porting of "Full Screen Responsive Image Slider | No Libraries" by Traversy Media
   * into Svelte
	 * see: https://www.youtube.com/watch?v=wWWNrANNO1k
	 * see: https://codepen.io/bradtraversy/pen/oVPBaa
	 */
	
	import Slides from './Slides.svelte';
	let showModal = false;
	function handleClick() {
		showModal = !showModal;
	}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Roboto&display=swap');
@import url('https://stackpath.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css');

:global(*) {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

:global(body) {
  font-family: 'Roboto', Arial, Helvetica, sans-serif;
  background-color: #333;
  color: #fff;
  line-height: 1.6;
}

.modal {
	background: black;
	position: absolute;
	z-index: 100;
	top: 0px;
	width: 100vw;
	height: 100vh;
	transform: translateY(-100vh);
	transition: all 300ms linear;
	opacity: 0;
}

.show-modal {
	transform:  translateY(0vh);
	opacity: 1;
}



</style>

<svelte:head>
	<title>Full Screen Slider</title>
</svelte:head>
<button on:click={handleClick}>Click</button>

	<div class="modal" class:show-modal={showModal}>
		<p>Text</p>

			<button on:click={handleClick}>
				close
			</button>
	</div>

<Slides auto={true} interval={5000}/>