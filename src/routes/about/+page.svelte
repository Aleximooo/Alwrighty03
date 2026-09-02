<script>
	/** @type {import('./$types').PageProps} */
	let { data } = $props();

	import Alex1 from '$lib/photos/IMG_8047.jpg';
	let isActive = $state(false);

// after this point we will load our scene and adjacent addons
	import { Canvas } from '@threlte/core'
	import Scene from './Scene.svelte'

  import { AsciiRenderer } from '@threlte/extras'

  let fgColor = $state('orange')
  let bgColor = $state('none')

// const defaultCharacters = ``.trim();

// let characters = $state(defaultCharacters)
//   let alpha = $state('true')
//   let block = $state('false')
//   let color = $state('true')
//   let invert = $state('false')
//   let resolution = $state('10')
//   let scale = $state('2')


</script>

<div id="bg">
  <Canvas>
    <!-- <AsciiRenderer
      {bgColor}
      {characters}
      {fgColor}
	  {alpha}
	  {block}
	  {color}
	  {invert}
	  {resolution}
	  {scale}
    /> -->
    <Scene />
  </Canvas>
</div>

<div>

	<image id="alex" src={Alex1} />

	<p>
		My name is Alex Wright and I'm a musician + producer from Orange, CT. I graduated from Berklee
		CoM. Stay tuned for my EP on July 8th!
	</p>

	<ul>
		<li class="email" class:active={isActive} onclick={() => (isActive = !isActive)}>
			<p>Contact me here</p>
			<a class:active={isActive}>alwrighty03@gmail.com</a>
		</li>
		<ul class="contacts" class:active={isActive}>
			<li><a>instagram</a></li>
			<li><a>bandmix</a></li>
			<li><a>soundcloud</a></li>
			<li><a>bandcamp</a></li>
			<li><a>gmail</a></li>
		</ul>
	</ul>
</div>

<style>

	#bg {
		position: fixed;
		width: 110vw;
		top: 0; left: 0;
		z-index: 2;
	}

	#alex {
		width: 30vh;
	}

	ul li {
		list-style: none;
		position: relative;
		/* outline: 1px solid black; */
		transition: 0.2s;
	}

	ul li::before {
		position: absolute;
		content: '';
		top: 0%;
		left: auto;
		right: auto;
		bottom: auto;
		height: 100%;
		width: 1em;
		border-left: 1px solid black;
		border-bottom: 1px solid black;
		transition: ease 0.2s;
	}

	.email {
		background: white;
		z-index: 2;
		cursor: pointer;
	}
	.email::before {
		margin-left: -1em;
		/* border-color: red; */
		z-index: 2;
	}
	.email:hover::before {
		top: 50%;
		height: 50%;
		width: 2em;
		border-bottom: 2px solid;
	}

	.email.active::before {
		top: 100%;
		height: 0%;
		width: 7em;
		border-bottom: 2px dashed black;
		border-left: black;
		margin-left: 0em;
	}

	.email a::before {
		right: 6em;
		transform-origin: left;
		transition: 0.2s;
	}

	.email.active a::before {
		transform: scaleX(1);
	}

	.contacts {
		visibility: hidden;
		z-index: -1;
		cursor: pointer;
		line-height: 2cap;
	}

	.contacts.active {
		visibility: visible;
	}

	.contacts li::before {
		width: 0;
		height: 0%;
		top: 0;
	}

	.contacts.active li::before {
		width: 0.5em;
		height: 50%;
		/* border-bottom: 1px solid red; */
	}

	.contacts :nth-child(1 of li) {
		top: -2cap;
		transition: ease 0.1s;
	}
	.contacts :nth-child(2 of li) {
		top: -4cap;
		transition: ease 0.2s;
	}
	.contacts :nth-child(3 of li) {
		top: -6cap;
		transition: ease 0.3s;
	}
	.contacts :nth-child(4 of li) {
		top: -8cap;
		transition: ease 0.4s;
	}
	.contacts :nth-child(5 of li) {
		top: -10cap;
		transition: ease 0.5s;
		/* margin-bottom: 10cap; */
	}

	.active.contacts li {
		top: 0;
	}

	.contacts a {
		font-family: monospace;
	}

	.active.contacts a {
		font-family: monospace;
		text-decoration: underline;
		padding-left: 1cap;
	}

	.contacts a::before {
		right: 0;
		transform-origin: left;
		transition: 0.2s;
	}


</style>
