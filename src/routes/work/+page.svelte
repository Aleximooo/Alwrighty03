<script>
	/** @type {import('./$types').PageProps} */
	let { data } = $props();

	let isActive = $state(false);
	let isActive2 = $state(false);
	let isActive3 = $state(false);
</script>

<ul>
	<li class="email" class:active={isActive} onclick={() => (isActive = !isActive)}>
		<a class:active={isActive}>alwrighty03@gmail.com</a>
	</li>
	<ul class="contacts" class:active={isActive}>
		<li><a>instagram</a></li>
		<li><a>bandmix</a></li>
		<li><a>soundcloud</a></li>
		<li><a>bandcamp</a></li>
		<li><a>gmail</a></li>
	</ul>

	<li
		class="email"
		class:move={isActive}
		class:active={isActive2}
		onclick={() => (isActive2 = !isActive2)}
	>
		<a class:active={isActive2}>alwrighty03@gmail.com</a>
	</li>
	<ul class="contacts" class:active={isActive2}>
		<li><a>instagram</a></li>
		<li><a>bandmix</a></li>
		<li><a>soundcloud</a></li>
		<li><a>bandcamp</a></li>
		<li><a>gmail</a></li>
	</ul>

	<li
		class="email"
		class:move={isActive2}
		class:active={isActive3}
		onclick={() => (isActive3 = !isActive3)}
	>
		<a class:active={isActive3}>alwrighty03@gmail.com</a>
	</li>
	<ul class="contacts" class:active={isActive3}>
		<li><a>instagram</a></li>
		<li><a>bandmix</a></li>
		<li><a>soundcloud</a></li>
		<li><a>bandcamp</a></li>
		<li><a>gmail</a></li>
	</ul>
</ul>

<style>
	ul li {
		list-style: none;
		position: relative;
		/* outline: 1px solid black; */
		transition: 0.4s;
		font-size: 1.5cap;
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

	.contacts li {
		/* visibility: hidden; */
		z-index: -1;
		cursor: pointer;
		line-height: 2cap;
	}

	.contacts.active li {
		top: 0;
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

	:nth-last-child(-n + 2 of .email) {
		margin-top: -9cap;
	}

	.email.move {
		margin-top: 1cap;
	}
</style>
