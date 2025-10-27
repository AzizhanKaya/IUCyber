<template>
	<section id="about">
		<div class="section-container about-container">
			<div class="about-image">
				<img src="https://images.unsplash.com/photo-1550751827-4bd374c3f58b?q=80&w=2070&auto=format&fit=crop" alt="Siber Güvenlik Çalışması" />
			</div>
			<div class="about-content">
				<h2 class="section-title">Biz <span>Kimiz?</span></h2>
				<p>
					Siber güvenlik alanında tutkulu, öğrenmeye ve öğretmeye adanmış bir grup teknoloji meraklısıyız. Amacımız, üyelerimizi siber dünyanın
					tehditlerine karşı bilinçlendirmek, onlara pratik beceriler kazandırmak ve bu alanda kariyer hedeflerine ulaşmalarına yardımcı olmaktır.
				</p>
				<br />
				<p>
					Linux'tan ağ güvenliğine, kriptografiden zararlı yazılım analizine kadar geniş bir yelpazede düzenlediğimiz HackOps akademisi eğitimleri ve
					seminerler ile üyelerimizin teknik becerilerini geliştiriyor, CTF (Capture The Flag) yarışmaları ile teorik bilgiyi pratiğe döküyoruz.
				</p>
			</div>
		</div>
	</section>
</template>

<style scoped>
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

	@media (max-width: 992px) {
		:deep(section) {
			padding: 6rem 5%;
		}
		.about-container {
			gap: 2rem;
		}
	}
	@media (max-width: 768px) {
		.about-container {
			flex-direction: column;
			text-align: center;
			gap: 3rem;
		}
		.about-content h2 {
			text-align: center;
		}
	}
</style>
