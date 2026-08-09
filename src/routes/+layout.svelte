<script>
    /** @type {import('./$types').LayoutProps} */
    let { data, children } = $props();
    import { page } from '$app/state';
    import '$lib/fonts.css';

</script>

<style>

:global(canvas) {
        position: absolute;
        z-index: -100;
}

    :global(*) {
        font-family: monospace;
        transition: .3s ease;
    }

    :global(a) {
    font-family: Univers;
    text-decoration: none;
    color: black;
    /* background-color: white; */
    /* padding: .25vw; */
    border-radius: .5vw;
    position: relative;
    z-index: 1;
    /* -webkit-user-drag: none; */
    }

    :global(a::before, 
    #name::before, 
    #sideheader::before) {
        transition: transform .2s ease;
        position: absolute;
        top:0;left:0;right:0;bottom:0;
        z-index: -10;
        transform: scaleX(0);
        transform-origin: left;
        content: " ";
        /* border-radius: 1vw; */
        background:dodgerblue;
        -moz-user-select:none;
    }

        :global(a:hover::before, 
        #sideheader:hover > #name::before, 
        #sideheader:hover > #sideheader::before) {
            transform: scaleX(1);
            transform-origin: right;
        }

    @keyframes shudder {

    }

    #header {
    background: if(
            media(width < 800px): orange;
            else: orange;
            );
    width: if(
            media(width < 800px): 80%;
            else: 40%;
            );
    margin-top: if(
            media(width < 800px): 4vw;
            else: 1vw
            );
    /* left: if(
            media(width < 800px): 1vw;
            else: 0;
            ); */
    position: relative;
    anchor-name: --header;
    margin: 1cap;
    justify-self: center;
    padding: 1cap;
    border-radius: 1vw;
    }

    #sideheader {
    background: if(
            media(width < 800px): orange;
            else: orange;
            );
    width: if(
            media(width < 800px): fit-content;
            else: 50%;
            );
    height: if(
            media(width < 800px): 3em;
            else: fit-content;
            );
    animation: if(
            media(width < 800px): wipe;
            else: wipe .7s;
            );
    justify-self: if(
            media(width < 800px): normal;
            else: center;
            );
    position-anchor: --header;
    left: if(
            media(width < 800px): calc(5%);
            else: 0;
            );
    position: if(
        media(width < 800px): absolute;
        else: relative;
        );
    padding: 1cap;
    border-radius: 1vw;
        transform: rotate(if(
                media(width < 800px): 90deg;
                else: 0deg
                ));
                    transform-origin: top left;        
    }    

        #name {
        font-family: if(
                media(width < 800px): monospace;
                else: LibreBarcode128-Text;
                );
                    color: black;
        font-size: if(
                media(width < 800px): 2em;
                else: 7.5vw;
                );
        justify-self: if(
                media(width < 800px): center;
                else: center;
                );
        bottom: if(
                media(width < 800px): calc(.25em + 1vw);
                else: auto;
                );
        vertical-align: if(
            media(width < 800px): bottom;
            else: baseline;
        );
        position: if(
                media(width < 800px): relative;
                else: relative
        );
        text-wrap-mode: nowrap;
        z-index: 1;
        font-weight: 500;
        vertical-align:top;
        -moz-user-select:none;

        margin: 0;
        }
        /* #name::before {
            mix-blend-mode:multiply;
            opacity: 50%;
            z-index: 2;
            background-color: blue;
        }
        #name:hover::before {} */

        /* a::before {}
        a:hover::before {} */

    :global(#middle) {
    width: if(
            media(width < 800px): 80%;
            else: 50%;
            );
    justify-self: center;
    background: none;
    /* outline: 1px dashed black; */
    padding: 1cap;
    border-radius: 1vw;
    }
    :global(img) {
        border-radius: 1vw;
    }

</style>

<div id="sideheader">
    <h1 id="name"> Alex Wright { page?.url?.pathname } </h1>
</div>

<div id="header">
    <nav>
        <a href="/about"> about </a>
        <a href="/work"> work </a>
    </nav>
</div>

<div id="middle">
{@render children()}
</div>