<template>
	<div id="cyber-club-app">
		<header class="main-header" :class="{ 'menu-open': isMenuOpen }">
			<nav class="navbar">
				<a href="#home" class="logo"> IU<span>Cyber</span> </a>

				<div class="hamburger-menu" @click="toggleMenu">
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

		<main>
			<section id="home" class="hero-section">
				<div class="hero-overlay"></div>
				<div class="hero-content">
					<h1 class="hero-title">Geleceğin Siber Kalkanları</h1>
					<p class="hero-subtitle">Dijital dünyanın sınırlarını korumak için buradayız.</p>
					<a href="#about" class="btn btn-primary">Daha Fazlasını Keşfet</a>
				</div>
			</section>

			<section id="about">
				<div class="section-container about-container">
					<div class="about-image">
						<img src="https://images.unsplash.com/photo-1550751827-4bd374c3f58b?q=80&w=2070&auto=format&fit=crop" alt="Siber Güvenlik Çalışması" />
					</div>
					<div class="about-content">
						<h2 class="section-title">Biz <span>Kimiz?</span></h2>
						<p>Biz, siber güvenlik alanında tutkulu, öğrenmeye ve öğretmeye adanmış bir grup teknoloji meraklısıyız. Amacımız, üyelerimizi siber dünyanın tehditlerine karşı bilinçlendirmek, onlara pratik beceriler kazandırmak ve bu alanda kariyer hedeflerine ulaşmalarına yardımcı olmaktır.</p>
						<p>Etik hacker'lıktan ağ güvenliğine, kriptografiden zararlı yazılım analizine kadar geniş bir yelpazede düzenlediğimiz atölye çalışmaları, seminerler ve CTF (Capture The Flag) yarışmaları ile teorik bilgiyi pratiğe döküyoruz.</p>
					</div>
				</div>
			</section>

			<section id="events">
				<div class="section-container">
					<h2 class="section-title">Yaklaşan <span>Etkinlikler</span></h2>
					<div class="events-grid">
						<div v-for="event in events" :key="event.id" class="event-card">
							<div class="card-image-container">
								<img :src="event.image" :alt="event.title" />
							</div>
							<div class="card-content">
								<span class="event-date">{{ event.date }}</span>
								<h3 class="card-title">{{ event.title }}</h3>
								<p class="card-description">{{ event.description }}</p>
							</div>
						</div>
						<div v-if="events.length === 0" class="no-events">
							<p>Yakın zamanda planlanmış bir etkinlik bulunmamaktadır.</p>
						</div>
					</div>
				</div>
			</section>

			<section id="team">
				<div class="section-container">
					<h2 class="section-title">Yönetim <span>Takımı</span></h2>
					<div class="team-grid">
						<div v-for="member in teamMembers" :key="member.id" class="team-card">
							<img :src="member.avatar" :alt="member.name" class="team-avatar" />
							<h3 class="member-name">{{ member.name }}</h3>
							<p class="member-role">{{ member.role }}</p>
						</div>
					</div>
				</div>
			</section>

			<section id="contact">
				<div class="section-container contact-container">
					<h2 class="section-title">Bize <span>Ulaşın</span></h2>
					<p>Sorularınız, önerileriniz veya iş birliği teklifleriniz için bizimle iletişime geçmekten çekinmeyin.</p>
					<div class="contact-info">
						<a href="mailto:iletisim@siberkulup.com" class="btn btn-secondary">iletisim@siberkulup.com</a>
					</div>
				</div>
			</section>
		</main>

		<footer class="main-footer-bottom">
			<p>&copy; {{ new Date().getFullYear() }} IUCyber Kulübü. Tüm hakları saklıdır.</p>
			<p>Tasarım & Geliştirme: Azizhan Kaya</p>
		</footer>
	</div>
</template>

<script setup>
	import { ref, onMounted, onUnmounted } from 'vue';

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
		margin-bottom: 2rem;
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

	.hero-section {
		background-image: url('https://images.unsplash.com/photo-1544256718-3bcf237f3974?q=80&w=2071&auto=format&fit=crop');
		background-size: cover;
		background-position: center;
		position: relative;
		text-align: center;
		display: flex;
		align-items: center;
		justify-content: center;
		color: white;
	}
	.hero-overlay {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background: linear-gradient(to bottom, rgba(10, 10, 10, 0.8), rgba(10, 10, 10, 0.95));
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

	.about-container {
		display: flex;
		align-items: center;
		gap: 4rem;
	}
	.about-image {
		flex: 1;
	}
	.about-image img {
		width: 100%;
		border-radius: 10px;
		border: 2px solid var(--border-color);
		box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
	}
	.about-content {
		flex: 1.2;
	}
	.about-content h2 {
		text-align: left;
	}

	#events {
		background-color: var(--surface-color);
	}
	.section-container {
		width: 100%;
		max-width: 1400px;
	}
	.events-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
		gap: 2rem;
	}
	.event-card {
		background: var(--background-color);
		border: 1px solid var(--border-color);
		border-radius: 8px;
		overflow: hidden;
		display: flex;
		flex-direction: column;
		transition: transform 0.3s ease, box-shadow 0.3s ease;
	}
	.event-card:hover {
		transform: translateY(-10px);
		box-shadow: 0 0 20px var(--primary-glow);
		border-color: var(--primary-color);
	}
	.card-image-container img {
		width: 100%;
		height: 200px;
		object-fit: cover;
		filter: grayscale(30%);
		transition: filter 0.3s ease;
	}
	.event-card:hover .card-image-container img {
		filter: grayscale(0%);
	}
	.card-content {
		padding: 1.5rem;
		flex-grow: 1;
		display: flex;
		flex-direction: column;
	}
	.event-date {
		color: var(--primary-color);
		font-size: 0.9rem;
		font-weight: 600;
		margin-bottom: 0.5rem;
	}
	.card-title {
		font-size: 1.4rem;
		margin-bottom: 0.8rem;
		color: var(--text-color);
	}
	.card-description {
		color: var(--text-muted-color);
		flex-grow: 1;
	}
	.no-events {
		color: var(--text-muted-color);
		text-align: center;
		grid-column: 1 / -1;
		padding: 2rem;
	}

	.team-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
		gap: 2rem;
		justify-content: center;
	}
	.team-card {
		text-align: center;
		transition: transform 0.3s ease;
	}
	.team-card:hover {
		transform: scale(1.05);
	}
	.team-avatar {
		width: 150px;
		height: 150px;
		border-radius: 50%;
		border: 3px solid var(--border-color);
		margin-bottom: 1rem;
		transition: border-color 0.3s ease, box-shadow 0.3s ease;
	}
	.team-card:hover .team-avatar {
		border-color: var(--primary-color);
		box-shadow: 0 0 15px var(--primary-glow);
	}
	.member-name {
		font-size: 1.2rem;
		margin-bottom: 0.25rem;
		color: var(--text-color);
	}
	.member-role {
		color: var(--primary-color);
		font-weight: 500;
	}

	#contact {
		background-color: var(--surface-color);
	}
	.contact-container {
		text-align: center;
		max-width: 700px;
	}
	.contact-container p {
		color: var(--text-muted-color);
		margin-bottom: 2rem;
		font-size: 1.1rem;
	}

	.main-footer-bottom {
		text-align: center;
		padding: 2rem;
		background-color: #000;
		color: var(--text-muted-color);
		font-size: 0.9rem;
	}

	@media (max-width: 992px) {
		section {
			padding: 6rem 5%;
		}
		.about-container {
			gap: 2rem;
		}
	}

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

		.hero-title {
			font-size: 2.8rem;
		}
		.hero-subtitle {
			font-size: 1.2rem;
		}

		.about-container {
			flex-direction: column;
			text-align: center;
			gap: 3rem;
		}
		.about-content h2 {
			text-align: center;
		}

		.section-title {
			font-size: 2rem;
		}
	}
</style>
