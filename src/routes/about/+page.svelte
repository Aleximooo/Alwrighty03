<script>
    /** @type {import('./$types').PageProps} */
    let { data } = $props();
    import Alex1 from '$lib/photos/IMG_8047.jpg';
	import { threeAdapter } from 'animejs/adapters/three';
    
    
    let isActive = $state(false);

    import * as THREE from 'three';
    import { OrbitControls } from "three/addons/controls/OrbitControls.js";
    import { GLTFLoader } from "three/addons/loaders/GLTFLoader.js";
    
	import { onMount } from 'svelte';
	onMount(async () => {

    const camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 0.1, 1000 );
    const scene = new THREE.Scene();
    const renderer = new THREE.WebGLRenderer({ 
        canvas: document.querySelector('#bg'),
        alpha: true 
    });
        renderer.setPixelRatio( window.devicePixelRatio );
        renderer.setSize( window.innerWidth, window.innerHeight );
        camera.position.setZ(5);

        renderer.render( scene, camera );

    const loader = new GLTFLoader();

        // const orange = new THREE.TorusKnotGeometry
        // const material = new THREE.MeshStandardMaterial( { color: 0xff9900 } );
        // const torus = new THREE.Mesh ( orange, material );
        //     scene.add(torus)

        const ambientLight = new THREE.DirectionalLight(0xffffff);
        const pointLight = new THREE.AmbientLight(0xff9900);
            pointLight.position.set(20, 0, 0);
                scene.add(pointLight, ambientLight);

        const lightHelper = new THREE.PointLightHelper(pointLight);
        const gridHelper = new THREE.GridHelper(200, 50);
            scene.add(lightHelper, gridHelper);


        const controls = new OrbitControls(camera, renderer.domElement);

        function addStar() {
            const orange = new THREE.SphereGeometry(0.25, 24, 24);
            const material = new THREE.MeshStandardMaterial({ color: 0xff9900 });
            const star = new THREE.Mesh( orange, material );

            const [x, y, z] = Array(3).fill().map(() => THREE.MathUtils.randFloatSpread( 100 ));

            star.position.set(x, y, z);
            scene.add(star)
        }

        Array(200).fill().forEach(addStar)

        function moveOrange() {
            const t = document.body.getBoundingClientRect().top;
            orange.rotation.x += 0.05;
            orange.rotation.y += 0.005;
            orange.rotation.z += 0.01;
        }

        function animate() {
            requestAnimationFrame( animate );

            controls.update();

            renderer.render ( scene, camera );
        }
        document.body.onscroll = moveOrange;
        animate();

        window.addEventListener( 'resize', onWindowResize, false );

        function onWindowResize(){

            camera.aspect = window.innerWidth / window.innerHeight;
            camera.updateProjectionMatrix();

            renderer.setSize( window.innerWidth, window.innerHeight );
            moveTorus();
        }
	});

</script>

<style>

    #bg {
        position: fixed;
        top: 0; left: 0;
        /* width: 12vlh; */
        z-index: -1;
    }
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
            height: 50%; width: 2em;
            border-bottom: 2px solid;
        }

        .email.active::before {
            top: 100%;
            height: 0%; width: 7em;
            border-bottom: 2px dashed black;
            border-left: black;
            margin-left: 0em;
        }

        .email a::before {
            right: 6em;
            transform-origin: left;
            transition: .2s;
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
            width: .5em;
            height: 50%;
            /* border-bottom: 1px solid red; */
        }

    .contacts :nth-child(1 of li){
        top: -2cap;
        transition: ease .1s;
    }
    .contacts :nth-child(2 of li){
        top: -4cap;
        transition: ease .2s;
    }
    .contacts :nth-child(3 of li){
        top: -6cap;
        transition: ease .3s;
    }
    .contacts :nth-child(4 of li){
        top: -8cap;
        transition: ease .4s;
    }
    .contacts :nth-child(5 of li){
        top: -10cap;
        transition: ease .5s;
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
            transition: .2s;
        }
</style>

<canvas id="bg"></canvas>

<image src={Alex1} style="width: 20%" />

<p>
    My name is Alex Wright and I'm 
    a musician + producer from 
    Orange, CT. I graduated from Berklee 
    CoM. Stay tuned for my EP on July 8th!
</p>

<ul>
    <li class="email" class:active={isActive}
	    onclick={() => isActive = !isActive}
    >
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