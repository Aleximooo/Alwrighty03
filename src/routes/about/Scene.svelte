<script>
    import { T } from '@threlte/core'
    import { 
        ContactShadows, Float, 
        Grid, OrbitControls,
        useDraco, useGltf,
    } from '@threlte/extras';


    const dracoLoader = useDraco()
    const gltf = useGltf('static/scene/Orange.gltf', { dracoLoader })

</script>



<T.PerspectiveCamera makeDefault position={[4, 1, 4]} fov={25}>
    <OrbitControls enableDamping
    />
</T.PerspectiveCamera>

<T.DirectionalLight intensity={1.8} position={[0, 10, 0]} castShadow shadow.bias={-0.0001} />
<T.AmbientLight intensity={1} />

{#await gltf then { scene }}
    <T is={scene} 
        position{[0, 0, 0]} 
        scale={0.01} 
        rotateX={2}
    />
{/await}

