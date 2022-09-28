<script>
	import { onMount } from 'svelte';
	import * as THREE from 'three';

	let container, pc;
	// Setting up the scene
	var scene = new THREE.Scene();

	let height = window.innerHeight - 51;
	let width = (window.innerWidth / 5) * 4;

	// Setting up a camera
	var camera = new THREE.PerspectiveCamera(100, width / height, 0.1, 50);
	camera.position.z = 30;

	// Setting up the renderer. This will be called later to render scene with the camera setup above
	var renderer = new THREE.WebGLRenderer({ antialias: true });
	renderer.setPixelRatio(window.devicePixelRatio);
	renderer.setSize(width, height);
	renderer.setClearColor(0x171717, 1);
	onMount(() => {
		container.appendChild(renderer.domElement);
	});

	// Setting up a group to hold the items we will be creating together
	var group = new THREE.Group();

	// Array curve holds the positions of points generated from a lorenz equation; lorenz function below generates the points and returns an array of points
	var arrayCurve = lorenz();

	// Generating the geometry
	var curve = new THREE.CatmullRomCurve3(arrayCurve);
	var geometry = new THREE.Geometry();
	geometry.vertices = curve.getPoints(100000);

	// Generating a cloud of point
	var pcMat = new THREE.PointsMaterial();
	pcMat.color = new THREE.Color(0x5ca755);
	pcMat.transparent = true;
	pcMat.size = 0.05;
	pcMat.blending = THREE.AdditiveBlending;
	pc = new THREE.Points(geometry, pcMat);
	pc.sizeAttenuation = false;
	pc.sortPoints = false;

	group.add(pc);

	scene.add(group);

	var prevFog = true;

	group.rotation.y += Math.PI / 2;

	var step = 0;

	var render = function () {
		renderer.render(scene, camera);
		requestAnimationFrame(render);

		//Varying the points on each frame
		step += 0.00001;
		var count = 0;
		var geometry = pc.geometry;
		var a = 0.9 + Math.random() * 6;
		var b = 3.4 + Math.random() * 7;
		var f = 9.9 + Math.random() * 8;
		var g = 1 + Math.random();
		var t = 0.001;

		geometry.vertices.forEach(function (v) {
			v.x = v.x - t * a * v.x + t * v.y * v.y - t * v.z * v.z + t * a * f;
			v.y = v.y - t * v.y + t * v.x * v.y - t * b * v.x * v.z + t * g;
			v.z = v.z - t * v.z + t * b * v.x * v.y + t * v.x * v.z;
		});
		geometry.verticesNeedUpdate = true;

		// group.rotation.x += 0.001;
		// group.rotation.y += 0.001;
		// group.rotation.z += 0.001;
	};

	window.addEventListener(
		'resize',
		function () {
			camera.aspect = width / height;
			camera.updateProjectionMatrix();
			renderer.setSize(width, height);
		},
		false
	);

	render();

	function lorenz() {
		var arrayCurve = [];

		var x = 0.01,
			y = 0.01,
			z = 0.01;
		var a = 0.9;
		var b = 3.4;
		var f = 9.9;
		var g = 1;
		var t = 0.001;
		for (var i = 0; i < 100000; i++) {
			var x1 = x;
			var y1 = y;
			var z1 = z;
			x = x - t * a * x + t * y * y - t * z * z + t * a * f;
			y = y - t * y + t * x * y - t * b * x * z + t * g;
			z = z - t * z + t * b * x * y + t * x * z;
			arrayCurve.push(new THREE.Vector3(x, y, z).multiplyScalar(1));
		}
		return arrayCurve;
	}
</script>

<div bind:this={container} class:geometry={true} />

<style>
	.geometry {
		overflow: hidden;
		opacity: 0.9;
	}
</style>
