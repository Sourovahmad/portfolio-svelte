<script lang="ts">
	const githubUrl = "https://github.com/sourovahmad";
	
	let mouseX = 0;
	let mouseY = 0;
  
	function handleMouseMove(event: MouseEvent) {
	  mouseX = event.clientX;
	  mouseY = event.clientY;
	}
  </script>
  
  <svelte:window on:mousemove={handleMouseMove}/>
  
  <div class="portfolio-container">
	<div class="cursor-glow" style="left: {mouseX}px; top: {mouseY}px;"></div>
	
	<div class="hero-section">
	  <div class="name-container">
		<h1 class="name">Sourov Ahmad</h1>
		<div class="title">Software Developer</div>
	  </div>
	</div>
  
	<div class="content-section">
	  <div class="about-section">
		<h2>About Me</h2>
		<p>I'm a passionate software developer focused on creating elegant solutions to complex problems. I love exploring new technologies and building innovative applications.</p>
	  </div>
  
	  <div class="links-section">
		<a href={githubUrl} target="_blank" rel="noopener noreferrer" class="github-link">
		  <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
			<path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"></path>
		  </svg>
		  GitHub
		</a>
	  </div>
	</div>
  </div>
  
  <style>
	.portfolio-container {
	  min-height: 100vh;
	  background: linear-gradient(135deg, #1a1a1a 0%, #2d2d2d 100%);
	  color: #ffffff;
	  padding: 2rem;
	  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
	  position: relative;
	  overflow: hidden;
	}
  
	.cursor-glow {
	  position: fixed;
	  width: 200px;
	  height: 200px;
	  background: radial-gradient(circle, rgba(0,255,135,0.05) 0%, rgba(96,239,255,0.05) 50%, transparent 70%);
	  border-radius: 50%;
	  pointer-events: none;
	  transform: translate(-50%, -50%);
	  z-index: 0;
	  transition: transform 0.1s ease-out;
	  filter: blur(8px);
	}
  
	.hero-section {
	  height: 60vh;
	  display: flex;
	  align-items: center;
	  justify-content: center;
	  position: relative;
	  overflow: hidden;
	}
  
	.name-container {
	  text-align: center;
	  position: relative;
	  z-index: 1;
	  transition: transform 0.3s ease;
	}
  
	.name-container:hover {
	  transform: scale(1.05);
	}
  
	.name {
	  font-size: 4rem;
	  font-weight: 800;
	  margin: 0;
	  background: linear-gradient(45deg, #00ff87, #60efff);
	  -webkit-background-clip: text;
	  -webkit-text-fill-color: transparent;
	  animation: glow 2s ease-in-out infinite alternate;
	  position: relative;
	}
  
	.name::after {
	  content: '';
	  position: absolute;
	  bottom: -10px;
	  left: 50%;
	  transform: translateX(-50%);
	  width: 0;
	  height: 3px;
	  background: linear-gradient(45deg, #00ff87, #60efff);
	  transition: width 0.3s ease;
	}
  
	.name-container:hover .name::after {
	  width: 100%;
	}
  
	.title {
	  font-size: 1.5rem;
	  color: #888;
	  margin-top: 1rem;
	  transition: color 0.3s ease;
	}
  
	.name-container:hover .title {
	  color: #00ff87;
	}
  
	.content-section {
	  max-width: 800px;
	  margin: 0 auto;
	  padding: 2rem;
	  position: relative;
	  z-index: 1;
	}
  
	.about-section {
	  background: rgba(255, 255, 255, 0.05);
	  padding: 2rem;
	  border-radius: 1rem;
	  backdrop-filter: blur(10px);
	  margin-bottom: 2rem;
	  transition: transform 0.3s ease, box-shadow 0.3s ease;
	}
  
	.about-section:hover {
	  transform: translateY(-5px);
	  box-shadow: 0 10px 30px rgba(0, 255, 135, 0.1);
	}
  
	.about-section h2 {
	  color: #00ff87;
	  margin-top: 0;
	  transition: transform 0.3s ease;
	}
  
	.about-section:hover h2 {
	  transform: scale(1.05);
	}
  
	.links-section {
	  display: flex;
	  justify-content: center;
	  gap: 1rem;
	}
  
	.github-link {
	  display: flex;
	  align-items: center;
	  gap: 0.5rem;
	  padding: 0.75rem 1.5rem;
	  background: rgba(255, 255, 255, 0.1);
	  border-radius: 0.5rem;
	  color: white;
	  text-decoration: none;
	  transition: all 0.3s ease;
	  position: relative;
	  overflow: hidden;
	}
  
	.github-link::before {
	  content: '';
	  position: absolute;
	  top: 0;
	  left: -100%;
	  width: 100%;
	  height: 100%;
	  background: linear-gradient(
		90deg,
		transparent,
		rgba(255, 255, 255, 0.2),
		transparent
	  );
	  transition: 0.5s;
	}
  
	.github-link:hover::before {
	  left: 100%;
	}
  
	.github-link:hover {
	  background: rgba(255, 255, 255, 0.2);
	  transform: translateY(-2px) scale(1.05);
	  box-shadow: 0 5px 15px rgba(0, 255, 135, 0.2);
	}
  
	@keyframes glow {
	  from {
		text-shadow: 0 0 10px rgba(0, 255, 135, 0.5),
					 0 0 20px rgba(0, 255, 135, 0.3),
					 0 0 30px rgba(0, 255, 135, 0.1);
	  }
	  to {
		text-shadow: 0 0 20px rgba(0, 255, 135, 0.8),
					 0 0 30px rgba(0, 255, 135, 0.5),
					 0 0 40px rgba(0, 255, 135, 0.3);
	  }
	}
  
	@media (max-width: 768px) {
	  .portfolio-container {
		padding: 1rem;
	  }
  
	  .name {
		font-size: 2.5rem;
	  }
  
	  .title {
		font-size: 1.2rem;
	  }
  
	  .content-section {
		padding: 1rem;
	  }
  
	  .about-section {
		padding: 1.5rem;
	  }
  
	  .cursor-glow {
		display: none;
	  }
	}
  </style>
	  