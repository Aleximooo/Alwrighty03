<script>
    /** @type {import('./$types').PageProps} */
    let { data } = $props();

    let isActive = $state(false);
    let isActive2 = $state(false);
    let isActive3 = $state(false);

</script>

<style>

    ul li{
        list-style: none;
        position: relative;
        /* outline: 1px solid black; */
        transition: .2s;

    }

    ul li::before {
        position: absolute;
        content: '';
        top: 0%;left: auto;right: auto;bottom: auto;
        height: 100%; width: 1em;
        border-left:1px solid black;
        border-bottom:1px solid black;
        transition: ease .2s;

    }

    .showcase {
        background: white;
        z-index: 2;
        cursor: pointer;
    
    }
        .showcase::before {
        margin-left: -1em;
            /* border-color: red; */
            z-index: 2;
        }
        .showcase:hover::before {
            top: 50%;
            height: 50%; width: 2em;
            border-bottom: 2px solid;
        }

        .showcase.active::before {
            top: 100%;
            height: 0%; width: 7em;
            border-bottom: 2px dashed black;
            border-left: black;
            margin-left: 0em;

        }

        .showcase a::before {
            right: 6em;
            transform-origin: left;
            transition: .2s;
        }

        .showcase.active a::before {
            transform: scaleX(1);
        }        

    .work {
        visibility: hidden;
        z-index: -1;
        cursor: pointer;
    }

        .work.active {
        visibility: visible;  
        }

        .work li::before {
            width: 0;
            height: 0%;
            top: 0;
        }

        .work.active li::before {
            width: .5em;
            height: 50%;
            /* border-bottom: 1px solid red; */
        }

    .work :nth-child(1 of li){
        top: -2cap;
        transition: ease .1s;
    }
    .work :nth-child(2 of li){
        top: -4cap;
        transition: ease .2s;
    }
    .work :nth-child(3 of li){
        top: -6cap;
        transition: ease .3s;
    }
    .work :nth-child(4 of li){
        top: -8cap;
        transition: ease .4s;
    }
    .work :nth-child(5 of li){
        top: -10cap;
        transition: ease .5s;
    }

        .active.work li {
            top: 0;
        }

        .work a {
            font-family: monospace;
        }

        .active.work a {
            font-family: monospace;
            text-decoration: underline;
            padding-left: 1cap;

        }        

        .work a::before {
            right: 0;
            transform-origin: left;
            transition: .2s;
        }

    
    /* .showcase:nth-child(2 of li){
        margin-top: -8cap;
    }

    .active.showcase:nth-child(2 of li){
        margin-top: 0;
    } */
</style>

<ul class="show">
    <li class="showcase" class:active={isActive}
	    onclick={() => isActive = !isActive}
    >
        <p>Contact me here</p>
        <a class:active={isActive}>alwrighty03@gmail.com</a>
    </li>
    <ul class="work" class:active={isActive}>
        <li><a>li1</a></li>
        <li><a>li2</a></li>
        <li><a>li3</a></li>
        <li><a>li4</a></li>
        <li><a>li5</a></li>
    </ul>
    <li class="showcase" class:active={isActive2}
	    onclick={() => isActive2 = !isActive2}
    >
        <a class:active={isActive2}>alwrighty03@gmail.com</a>
    </li>
    <ul class="work" class:active={isActive2}>
        <li><a>li1</a></li>
        <li><a>li2</a></li>
        <li><a>li3</a></li>
        <li><a>li4</a></li>
        <li><a>li5</a></li>
    </ul>
    <li class="showcase" class:active={isActive3}
	    onclick={() => isActive3 = !isActive3}
    >
        <a class:active={isActive3}>alwrighty03@gmail.com</a>
    </li>
    <ul class="work" class:active={isActive3}>
        <li><a>li1</a></li>
        <li><a>li2</a></li>
        <li><a>li3</a></li>
        <li><a>li4</a></li>
        <li><a>li5</a></li>
    </ul>
</ul>