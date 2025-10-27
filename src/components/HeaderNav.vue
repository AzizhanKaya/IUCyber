<template>
	<header class="main-header" :class="{ 'menu-open': isMenuOpen }">
		<nav class="navbar">
			<a href="#home" class="logo"> IU<span>Cyber</span> </a>

			<div class="hamburger-menu" @click="$emit('toggle')">
				<span></span>
				<span></span>
				<span></span>
			</div>

			<ul class="nav-links">
				<li>
					<a href="#home" :class="{ active: activeSection === 'home' }">Anasayfa</a>
				</li>
				<li>
					<a href="#about" :class="{ active: activeSection === 'about' }">Hakkımızda</a>
				</li>
				<li>
					<a href="#events" :class="{ active: activeSection === 'events' }">Etkinlikler</a>
				</li>
				<li>
					<a href="#team" :class="{ active: activeSection === 'team' }">Takım</a>
				</li>
				<li>
					<a href="#contact" :class="{ active: activeSection === 'contact' }">İletişim</a>
				</li>
			</ul>
		</nav>
	</header>
</template>

<script setup>
	const props = defineProps({
		activeSection: { type: String, required: true },
		isMenuOpen: { type: Boolean, required: true },
	});
</script>

<style scoped>
	.main-header {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		z-index: 1000;
		padding: 1rem 5%;
		background: rgba(10, 10, 10, 0.7);
		backdrop-filter: blur(10px);
		-webkit-backdrop-filter: blur(10px);
		border-bottom: 1px solid var(--border-color);
		transition: background 0.3s ease;
	}
	.navbar {
		display: flex;
		justify-content: space-between;
		align-items: center;
		max-width: 1400px;
		margin: 0 auto;
	}
	.logo {
		font-size: 1.8rem;
		font-weight: 900;
		color: var(--text-color);
		text-decoration: none;
	}
	.logo span {
		color: var(--primary-color);
		text-shadow: 0 0 8px var(--primary-glow);
	}
	.nav-links {
		list-style: none;
		display: flex;
		gap: 2rem;
	}
	.nav-links a {
		color: var(--text-color);
		text-decoration: none;
		font-weight: 500;
		padding: 5px 0;
		position: relative;
		transition: color 0.3s ease;
	}
	.nav-links a::after {
		content: '';
		position: absolute;
		bottom: 0;
		left: 0;
		width: 0;
		height: 2px;
		background-color: var(--primary-color);
		transition: width 0.3s ease;
	}
	.nav-links a:hover,
	.nav-links a.active {
		color: var(--primary-color);
	}
	.nav-links a:hover::after,
	.nav-links a.active::after {
		width: 100%;
	}

	/* Mobile nav */
	@media (max-width: 768px) {
		.hamburger-menu {
			display: flex;
			flex-direction: column;
			justify-content: space-around;
			width: 2rem;
			height: 2rem;
			background: transparent;
			border: none;
			cursor: pointer;
			padding: 0;
			z-index: 10;
		}
		.hamburger-menu span {
			width: 2rem;
			height: 0.25rem;
			background: var(--text-color);
			border-radius: 10px;
			transition: all 0.3s linear;
			position: relative;
			transform-origin: 1px;
		}

		.nav-links {
			display: none;
			position: absolute;
			top: 100%;
			left: 0;
			width: 100%;
			background: rgba(10, 10, 10, 0.95);
			backdrop-filter: blur(10px);
			-webkit-backdrop-filter: blur(10px);
			flex-direction: column;
			align-items: center;
			padding: 2rem 0;
			gap: 1.5rem;
		}

		.main-header.menu-open .nav-links {
			display: flex;
		}

		.main-header.menu-open .hamburger-menu span:nth-child(1) {
			transform: rotate(45deg);
		}
		.main-header.menu-open .hamburger-menu span:nth-child(2) {
			opacity: 0;
			transform: translateX(20px);
		}
		.main-header.menu-open .hamburger-menu span:nth-child(3) {
			transform: rotate(-45deg);
		}
	}
</style>
