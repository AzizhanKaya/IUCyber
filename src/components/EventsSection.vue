<template>
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
</template>

<script setup>
	import eventsJson from '../../assets/events.json';
	import { ref } from 'vue';

	const events = ref(eventsJson);
</script>

<style scoped>
	#events {
		background-color: var(--surface-color);
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
</style>
