<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>

<script>
	import * as THREE from 'three';
	import * as SC from 'svelte-cubed';

	let width = 1;
	let height = 1;
	let depth = 1;

	let spin = 0;

	SC.onFrame(() => {
		spin += 0.01;
	});

</script>


<SC.Canvas antialias background={new THREE.Color('papayawhip')}> <!-- Adding Background to the Canvas / Scene -->
	<SC.Mesh geometry={new THREE.BoxGeometry()}
	material={new THREE.MeshStandardMaterial({ color: 0xff3e00})}
	scale={[width, height, depth]}
	rotation={[0, spin, 0]} castShadow
	/> <!-- Placing a BoxGeometry into the scene with standar mesh -->
	<SC.PerspectiveCamera position={[1, 1, 3]} /> <!-- Camera positioning -->
    <SC.OrbitControls enableZoom={false} /> <!-- Makes cube able to be spinned. -->
	<SC.AmbientLight intensity={0.6} />
	<SC.DirectionalLight intensity={0.6} position={[-2, 3, 2]} />
​</SC.Canvas>

<div class="controls">
	<label><input type="range" bind:value={width} min={0.1} max={3} step={0.1}>width</label>
	<label><input type="range" bind:value={height} min={0.1} max={3} step={0.1}>height</label>
	<label><input type="range" bind:value={depth} min={0.1} max={3} step={0.1}>depth</label>
</div>

<style>
	.controls {
		position: absolute;
	}
</style>
