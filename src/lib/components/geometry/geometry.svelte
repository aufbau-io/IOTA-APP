<script>
	import { onMount } from 'svelte';
	import * as THREE from 'three';
	let group;

	let container;

	let camera, scene, renderer;

	let mouseX = 0,
		mouseY = 0;

	let width = window.innerWidth /4 * 3
	let height = window.innerHeight - 51

	let coreAspect_1, coreAspect_2

	let windowHalfX = width / 2;
	let windowHalfY = height / 2;

	init();
	animate();

	function init() {
		camera = new THREE.PerspectiveCamera(20, width / height, 1, 10000);
		camera.position.z = 1200;

		scene = new THREE.Scene();
		scene.background = new THREE.Color(0x212121);

		const light = new THREE.DirectionalLight(0xf0f0f0);
		light.position.set(0, 1, 1);
		scene.add(light);

		// -------------------------------------------------------------------------



    coreAspect_1 = new THREE.Mesh( 
			new THREE.SphereGeometry( 170, 124, 62 ),
  		new THREE.MeshBasicMaterial( { color: 0x5ca755, wireframe: true } )
		)

		coreAspect_2 = new THREE.Mesh( 
			new THREE.SphereGeometry( 170, 124, 62 ),
  		new THREE.MeshBasicMaterial( { color: 0x5ca755, wireframe: true } )
		)

		screen = new THREE.Mesh( 
			new THREE.PlaneGeometry( 1000, 1000 ),
      new THREE.MeshBasicMaterial( { color: 0x212121, side: THREE.DoubleSide } )
			)

    
		
		scene.add( coreAspect_1 )
		scene.add( coreAspect_2 )
		scene.add( screen )
		
    scene.rotation.z += Math.PI/2
		scene.rotation.y += Math.PI










		// -------------------------------------------------------------------------

		renderer = new THREE.WebGLRenderer({ antialias: true });
		renderer.setPixelRatio(window.devicePixelRatio);
		renderer.setSize(width, height);

		onMount(() => {
			container.appendChild(renderer.domElement);
		});

		document.addEventListener('mousemove', onDocumentMouseMove);

		//

		window.addEventListener('resize', onWindowResize);
	}

	function onWindowResize() {
		windowHalfX = width / 2;
		windowHalfY = height / 2;

		camera.aspect = width / height;
		camera.updateProjectionMatrix();

		renderer.setSize(width, height);
	}

	function onDocumentMouseMove(event) {
		mouseX = event.clientX - windowHalfX;
		mouseY = event.clientY - windowHalfY;
	}

	function animate() {
		requestAnimationFrame(animate);

		coreAspect_1.rotation.x -= 0.0001
    coreAspect_1.rotation.z -= 0.0001

    coreAspect_2.rotation.x += 0.0001
		coreAspect_2.rotation.z += 0.0001

		render();
	}

	function render() {

		renderer.render(scene, camera);
	}
</script>

<div bind:this={container} class:geometry={true} />

<style>
	.geometry {
		overflow: hidden;
		opacity: .9;
	}
</style>
