<script>
    /** @type {import('./$types').LayoutProps} */
    let { data, children } = $props();
    import { page } from '$app/state';
	import { svelte } from '@sveltejs/vite-plugin-svelte';
    import '$lib/fonts/fonts.css';
</script>

<style>

    :global(*) {
        font-family: monospace;
        transition: transform .3s ease;
    }

    :global(::before) {
        transition: transform .2s ease;
        display: block;
        position: absolute;
        top:0;left:0;right:0;bottom:0;
        z-index: -1;
        transform: scaleX(0);
        transform-origin: center;
        content: " ";
        background: white;
    }
        :global(:hover::before) {
            transform: scaleX(1);
            transform-origin: center;
        }

    :global(a) {
        /* font-family: helvetica; */
        text-decoration: none;
        color: black;
        /* background-color: white; */
        padding: .25vw;
        border-radius: .5vw;
        position: relative;
        z-index: 1;
        }
        a::before {}
        a:hover::before {}

    #header {
        background: orange;
        justify-self: center;
        width: flex;
        padding: 1vw;
        border-radius: 1vw;
        user-select: none;
    }
        #name {
            font-family: Libre128;
            color: black;
            font-size: minmax(20vw, 3em);
            position: relative;
            z-index: 1;
        }
        #name::before {}
        #name:hover::before {}
</style>

<div id="header">
    <h1 id="name"> Alex Wright { page?.url?.pathname } </h1>
    <nav>
        <a href="/about"> about </a>
        <a href="/work"> work </a>
        <a href="/index"> index </a>
    </nav>
</div>

{@render children()}