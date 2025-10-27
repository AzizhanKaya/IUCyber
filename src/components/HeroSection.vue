<template>
	<section id="home" class="hero-section">
		<div class="hero-overlay"></div>
		<div class="hero-content">
			<h1 class="hero-title">Geleceğin Siber Kalkanları</h1>
			<p class="hero-subtitle">Dijital dünyanın sınırlarını korumak için buradayız.</p>
			<a href="#about" class="btn btn-primary">Daha Fazlasını Keşfet</a>
		</div>
	</section>
</template>

<style scoped>
	.hero-section {
		background-image: url('/logo.webp');
		background-size: 50%;
		background-color: #000;
		background-position: 50% 20%;
		background-repeat: no-repeat;
		position: relative;
		text-align: center;
		display: flex;
		align-items: center;
		justify-content: center;
		color: white;
	}

	@media (max-width: 768px) {
		.hero-section {
			background-size: 100%;
			background-position: 50% 50%;
		}
	}

	.hero-overlay {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background: linear-gradient(to bottom, rgba(10, 10, 10, 0.5), rgba(10, 10, 10, 0.8));
	}
	.hero-content {
		position: relative;
		z-index: 2;
	}
	.hero-title {
		font-size: 4rem;
		margin-bottom: 1rem;
		text-shadow: 0 0 10px var(--primary-glow), 0 0 20px var(--primary-glow);
	}
	.hero-subtitle {
		font-size: 1.5rem;
		font-weight: 300;
		margin-bottom: 2rem;
		color: var(--text-color);
	}

	@media (max-width: 768px) {
		.hero-title {
			font-size: 2.8rem;
		}
		.hero-subtitle {
			font-size: 1.2rem;
		}
	}
</style>
