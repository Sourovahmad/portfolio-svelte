<script>
	import { onMount } from 'svelte';

	let canvas;
	let ctx;
	let particles = [];

	const GITHUB_URL = 'https://github.com/sourovahmad';


	onMount(() => {
		if (typeof window === 'undefined') return;

		ctx = canvas.getContext('2d');
		resizeCanvas();

		window.addEventListener('resize', resizeCanvas);
		window.addEventListener('mousemove', handleMouseMove);

		animate();

		return () => {
			window.removeEventListener('resize', resizeCanvas);
			window.removeEventListener('mousemove', handleMouseMove);
		};
	});

	function resizeCanvas() {
		canvas.width = window.innerWidth;
		canvas.height = window.innerHeight;
	}

	function handleMouseMove(e) {
		for (let i = 0; i < 5; i++) {
			particles.push({
				x: e.clientX,
				y: e.clientY,
				vx: (Math.random() - 0.5) * 4,
				vy: (Math.random() - 0.5) * 4,
				size: Math.random() * 4 + 1,
				life: 100,
				hue: Math.random() * 360
			});
		}
	}

	function animate() {
		requestAnimationFrame(animate);

		// Fade effect for motion trails
		ctx.fillStyle = 'rgba(0, 0, 0, 0.1)';
		ctx.fillRect(0, 0, canvas.width, canvas.height);

		particles.forEach((p, index) => {
			p.x += p.vx;
			p.y += p.vy;
			p.life--;

			ctx.beginPath();
			ctx.fillStyle = `hsla(${p.hue}, 100%, 70%, ${p.life / 100})`;
			ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2);
			ctx.fill();

			if (p.life <= 0) {
				particles.splice(index, 1);
			}
		});
	}
</script>

<style>
	:global(body) {
		margin: 0;
		padding: 0;
		background: #000;
		overflow: hidden;
		font-family: 'Orbitron', sans-serif;
		cursor: none;
	}

	canvas {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		z-index: 0;
	}

	.overlay {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		text-align: center;
		color: white;
		z-index: 2;
		pointer-events: none;
	}

	h1 {
		font-size: 3.5rem;
		background: linear-gradient(90deg, #00ffe7, #ff00f7);
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent;
		text-shadow: 0 0 10px rgba(0, 255, 231, 0.4);
		animation: glow 2s ease-in-out infinite alternate;
	}

	@keyframes glow {
		from { text-shadow: 0 0 10px #00ffe7; }
		to { text-shadow: 0 0 30px #ff00f7; }
	}

	.github-link {
		margin-top: 2rem;
		pointer-events: auto;
		text-decoration: none;
		color: #00ffe7;
		font-size: 1.2rem;
		border: 1px solid #00ffe7;
		padding: 0.75rem 1.5rem;
		border-radius: 50px;
		transition: all 0.3s ease;
		backdrop-filter: blur(4px);
		box-shadow: 0 0 15px #00ffe755;
	}

	.github-link:hover {
		color: black;
		background: #00ffe7;
		box-shadow: 0 0 30px #00ffe7;
	}
</style>

<canvas bind:this={canvas}></canvas>

<div class="overlay">
	<h1>Im YOU or Not YOU Also Im ME </h1>
	<a class="github-link" href={GITHUB_URL} target="_blank" rel="noopener noreferrer">
		Visit GitHub
	</a>
</div>
