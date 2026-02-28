<template>
	<div>
		<HeaderNav :active-section="activeSection" :is-menu-open="isMenuOpen" @toggle="toggleMenu" />

		<main>
			<HeroSection />
			<AboutSection />
			<EventsSection :events="events" />
			<TeamSection />
			<ContactSection />
		</main>

		<FooterBottom />
	</div>
</template>

<script setup>
	import { ref, onMounted, onUnmounted } from 'vue';
	import HeaderNav from './components/HeaderNav.vue';
	import HeroSection from './components/HeroSection.vue';
	import AboutSection from './components/AboutSection.vue';
	import EventsSection from './components/EventsSection.vue';
	import TeamSection from './components/TeamSection.vue';
	import ContactSection from './components/ContactSection.vue';
	import FooterBottom from './components/FooterBottom.vue';

	const isMenuOpen = ref(false);
	const toggleMenu = () => {
		isMenuOpen.value = !isMenuOpen.value;
	};

	const events = ref([
		{
			id: 1,
			title: 'Capture The Flag (CTF) Yarışması',
			date: '15 Ağustos 2025',
			description: 'Siber güvenlik becerilerinizi test edeceğiniz, ödüllü bayrağı yakala yarışmamıza hazır olun!',
			image: 'https://images.unsplash.com/photo-1510915228340-29c85a43dcfe?q=80&w=2070&auto=format&fit=crop',
		},
		{
			id: 2,
			title: 'Web Güvenliği ve Zafiyetleri Atölyesi',
			date: '25 Eylül 2025',
			description: 'SQL Injection, XSS gibi temel web zafiyetlerini uygulamalı olarak öğreneceğimiz interaktif bir atölye.',
			image: 'https://vizyonergenc.com/storage/posts/September2019/XNtbVfGeL38TT7iwX0Xp.png',
		},
		{
			id: 3,
			title: 'Kriptografiye Giriş Semineri',
			date: '10 Ekim 2025',
			description: 'Şifreleme biliminin temellerini, tarihini ve modern dünyadaki önemini keşfedeceğimiz bir seminer.',
			image: 'https://images.unsplash.com/photo-1526374965328-7f61d4dc18c5?q=80&w=2070&auto=format&fit=crop',
		},
	]);

	const teamMembers = ref([
		{
			id: 1,
			name: 'Ahmet Faruk',
			role: 'Başkan',
			avatar: 'https://cdn.pixabay.com/photo/2015/10/05/22/37/blank-profile-picture-973460_960_720.png',
		},
		{
			id: 2,
			name: 'Bora Aksoy',
			role: 'Başkan Yardımcısı',
			avatar: 'https://cdn.pixabay.com/photo/2015/10/05/22/37/blank-profile-picture-973460_960_720.png',
		},
		{
			id: 3,
			name: 'Can Demir',
			role: 'Etkinlik Sorumlusu',
			avatar: 'https://cdn.pixabay.com/photo/2015/10/05/22/37/blank-profile-picture-973460_960_720.png',
		},
		{
			id: 4,
			name: 'Azizhan',
			role: 'Web Geliştirici',
			avatar: 'https://cdn.pixabay.com/photo/2015/10/05/22/37/blank-profile-picture-973460_960_720.png',
		},
	]);

	const activeSection = ref('home');
	let observer;

	onMounted(() => {
		const sections = document.querySelectorAll('section');

		const options = {
			root: null,
			rootMargin: '0px',
			threshold: 0.5,
		};

		observer = new IntersectionObserver((entries) => {
			entries.forEach((entry) => {
				if (entry.isIntersecting) {
					activeSection.value = entry.target.id;
				}
			});
		}, options);

		sections.forEach((section) => {
			observer.observe(section);
		});
	});

	onUnmounted(() => {
		if (observer) {
			observer.disconnect();
		}
	});
</script>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@700;900&family=Poppins:wght@300;400;600&display=swap');

	:root {
		--primary-color: #e50914;
		--primary-glow: rgba(229, 9, 20, 0.7);
		--background-color: #0a0a0a;
		--surface-color: #141414;
		--text-color: #f5f5f5;
		--text-muted-color: #888;
		--border-color: #2a2a2a;
	}

	* {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
	}

	html {
		scroll-behavior: smooth;
	}

	body {
		font-family: 'Poppins', sans-serif;
		background-color: var(--background-color);
		color: var(--text-color);
		line-height: 1.6;
	}

	h1,
	h2,
	h3,
	.logo {
		font-family: 'Orbitron', sans-serif;
	}

	.section-title {
		font-size: 2.5rem;
		margin-bottom: 3rem;
		text-align: center;
		text-transform: uppercase;
		letter-spacing: 2px;
	}
	.section-title span {
		color: var(--primary-color);
		text-shadow: 0 0 8px var(--primary-glow);
	}

	section {
		min-height: 100vh;
		padding: 8rem 5%;
		display: flex;
		justify-content: center;
		align-items: center;
		animation: fadeIn 1s ease-in-out;
	}

	@keyframes fadeIn {
		from {
			opacity: 0;
			transform: translateY(20px);
		}
		to {
			opacity: 1;
			transform: translateY(0);
		}
	}

	.btn {
		display: inline-block;
		padding: 0.8rem 1.8rem;
		border-radius: 5px;
		text-decoration: none;
		font-weight: 600;
		transition: all 0.3s ease;
		cursor: pointer;
		text-transform: uppercase;
		letter-spacing: 1px;
	}
	.btn-primary {
		background-color: var(--primary-color);
		color: white;
		border: 2px solid var(--primary-color);
	}
	.btn-primary:hover {
		background-color: transparent;
		color: var(--primary-color);
		transform: scale(1.05);
		box-shadow: 0 0 15px var(--primary-glow);
	}
	.btn-secondary {
		background-color: transparent;
		color: var(--text-color);
		border: 2px solid var(--border-color);
	}
	.btn-secondary:hover {
		background-color: var(--primary-color);
		border-color: var(--primary-color);
		color: white;
		transform: scale(1.05);
		box-shadow: 0 0 15px var(--primary-glow);
	}

	.section-container {
		width: 100%;
		max-width: 1400px;
	}

	@media (max-width: 992px) {
		section {
			padding: 6rem 5%;
		}
	}

	* {
		-webkit-tap-highlight-color: transparent;
	}
</style>
