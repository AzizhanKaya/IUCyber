<template>
	<section id="team">
		<div class="section-container">
			<Swiper
				:modules="[Navigation, Pagination, Autoplay]"
				:navigation="{
					nextEl: '.swiper-button-next',
					prevEl: '.swiper-button-prev',
				}"
				:pagination="{ clickable: true }"
				:loop="true"
				:autoplay="{
					delay: 4000,
					disableOnInteraction: true,
				}"
				:autoHeight="true"
				@slideChange="onSlideChange"
				class="team-swiper"
			>
				<SwiperSlide v-for="(team, teamName) in teams" :key="teamName">
					<div class="team-slide">
						<h2 class="team-title">
							<span v-for="(word, index) in teamName.split(' ')" :key="index" :class="{ 'text-primary': index % 2 === 0 }">
								{{ word }}
							</span>
						</h2>
						<div class="team-container">
							<div v-for="(member, index) in team" :key="index" class="team-card">
								<img :src="`members/${member.name}.png`" :alt="member.name" class="team-avatar" />
								<h3 class="member-name">{{ member.name }}</h3>
								<p class="member-role">{{ member.role }}</p>
							</div>
						</div>
					</div>
				</SwiperSlide>

				<div class="swiper-button-prev team-nav-button"></div>
				<div class="swiper-button-next team-nav-button"></div>
			</Swiper>
		</div>
	</section>
</template>

<script setup>
	import { ref, computed } from 'vue';
	import { Swiper, SwiperSlide } from 'swiper/vue';
	import { Navigation, Pagination, Autoplay } from 'swiper/modules';
	import 'swiper/css';
	import 'swiper/css/navigation';
	import 'swiper/css/pagination';
	import membersJson from '../../assets/members.json';

	const teams = ref(membersJson);
	const activeTeamIndex = ref(0);

	const onSlideChange = (swiper) => {
		activeTeamIndex.value = swiper.activeIndex;
	};
</script>

<style scoped>
	#team {
		padding-top: 6rem;
	}

	.team-swiper {
		width: 100%;
		height: auto;
		padding-bottom: 4rem;
	}

	.team-container {
		display: flex;
		flex-wrap: wrap;
		justify-content: center;
		gap: 2rem;
		max-width: 1200px;
		padding: 2rem 4rem;
		margin: 0 auto;
	}

	.team-card {
		text-align: center;
		padding: 1.5rem 1.5rem;
		transition: all 0.3s ease;
		border-radius: 8px;
		background: rgba(255, 255, 255, 0.02);
		border: 1px solid var(--border-color);
		width: 250px;
		flex: 0 0 auto;
		max-width: 100%;
	}

	.team-card:hover {
		transform: translateY(-5px);
		box-shadow: 0 0 20px rgba(229, 9, 20, 0.3);
		border-color: var(--primary-color);
	}

	.team-avatar {
		width: 150px;
		height: 150px;
		border-radius: 50%;
		border: 3px solid var(--border-color);
		transition: all 0.3s ease;
		object-fit: cover;
	}

	.team-card:hover .team-avatar {
		border-color: var(--primary-color);
		box-shadow: 0 0 15px var(--primary-glow);
	}

	.team-title {
		font-size: 2.5rem;
		text-align: center;
		text-transform: uppercase;
		letter-spacing: 2px;
		display: flex;
		flex-wrap: wrap;
		justify-content: center;
		align-items: center;
	}

	.team-title span {
		transition: all 0.3s ease;
	}

	.team-title span:not(:last-child) {
		margin-right: 0.5rem;
	}

	.team-title .text-primary {
		color: var(--primary-color);
		text-shadow: 0 0 8px var(--primary-glow);
	}

	.member-name {
		font-size: 1.2rem;
		margin: 0.5rem 0 0.25rem;
		color: var(--text-color);
		font-weight: 600;
	}

	.member-role {
		color: var(--primary-color);
		font-weight: 500;
		font-size: 0.9rem;
		margin: 0;
	}

	.team-nav-button {
		color: var(--text-color);
		cursor: pointer;
		transition: all 0.3s ease;
		backdrop-filter: blur(5px);
	}

	.team-nav-button::after {
		font-size: 1.5rem;
		font-weight: bold;
	}

	.team-nav-button:hover {
		color: var(--primary-color);
	}

	.team-nav-button:hover::after {
		box-shadow: 0 0 10px var(--primary-glow), 0 0 20px var(--primary-glow);
	}

	.swiper-button-prev {
		left: 20px;
	}

	.swiper-button-next {
		right: 20px;
	}

	:deep(.swiper-pagination) {
		position: relative;
		height: 30px;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	:deep(.swiper-pagination-bullet) {
		width: 12px;
		height: 12px;
		background: transparent;
		border: 2px solid var(--border-color);
		opacity: 1;
		margin: 0 5px;
		transition: all 0.3s ease;
	}

	:deep(.swiper-pagination-bullet-active) {
		background: var(--primary-color);
		border-color: var(--primary-color);
		box-shadow: 0 0 10px var(--primary-glow);
		transform: scale(1.2);
	}

	:deep(.swiper-pagination-bullet) {
		width: 12px;
		height: 12px;
		background: transparent;
		border: 2px solid var(--border-color);
		opacity: 1;
		margin: 0 5px;
		transition: all 0.3s ease;
	}

	:deep(.swiper-pagination-bullet-active) {
		background: var(--primary-color);
		border-color: var(--primary-color);
		box-shadow: 0 0 10px var(--primary-glow);
		transform: scale(1.2);
	}

	@media (max-width: 768px) {
		.team-avatar {
			width: 120px;
			height: 120px;
		}

		.team-container {
			display: grid;
			grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
			gap: 1rem;
			padding: 2rem;
		}

		.team-card {
			padding: 1rem 0.5rem;
		}

		.member-name {
			font-size: 1.1rem;
		}

		.member-role {
			font-size: 0.85rem;
		}

		.team-nav-button {
			width: 40px;
			height: 40px;
		}

		.team-nav-button::after {
			font-size: 1.2rem;
		}

		.swiper-button-prev {
			display: none;
		}

		.swiper-button-next {
			display: none;
		}

		#team {
			padding: 6rem 0rem;
		}
	}
</style>
