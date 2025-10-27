<template>
	<section id="contact">
		<div class="section-container">
			<h2 class="section-title">Bize <span>Ulaşın</span></h2>
			<p class="contact-subtitle">Sorularınız, önerileriniz veya iş birliği teklifleriniz için bizimle iletişime geçmekten çekinmeyin.</p>

			<div class="contact-cards">
				<a href="https://www.linkedin.com/company/iucyberofficial" target="_blank" class="contact-card linkedin">
					<div class="card-icon">
						<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor">
							<path
								d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"
							/>
						</svg>
					</div>
					<h3>LinkedIn</h3>
					<p>/iucyberofficial</p>
				</a>

				<a href="https://www.instagram.com/iucyberofficial" target="_blank" class="contact-card instagram">
					<div class="card-icon">
						<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor">
							<path
								d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"
							/>
						</svg>
					</div>
					<h3>Instagram</h3>
					<p>@iucyberofficial</p>
				</a>

				<a href="mailto:iletisim@iucyber.com" class="contact-card email">
					<div class="card-icon">
						<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor">
							<path d="M12 12.713l-11.985-9.713h23.97l-11.985 9.713zm0 2.574l-12-9.725v15.438h24v-15.438l-12 9.725z" />
						</svg>
					</div>
					<h3>E-posta</h3>
					<p>iletisim@iucyber.com</p>
				</a>
			</div>
		</div>
	</section>
</template>

<style scoped>
	#contact {
		background-color: var(--surface-color);
		padding: 5rem 0;
	}

	.contact-subtitle {
		color: var(--text-muted-color);
		margin: 1rem auto 3rem;
		max-width: 700px;
		font-size: 1.1rem;
		line-height: 1.6;
		text-align: center;
	}

	.contact-cards {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
		gap: 2rem;
		max-width: 1200px;
		margin: 0 auto;
		padding: 0 1rem;
	}

	.contact-card {
		background: rgba(255, 255, 255, 0.02);
		border: 1px solid var(--border-color);
		border-radius: 12px;
		padding: 2.5rem 2rem;
		text-align: center;
		transition: all 0.3s ease;
		text-decoration: none;
		color: var(--text-color);
		display: flex;
		flex-direction: column;
		align-items: center;
		height: 100%;
		position: relative;
		overflow: hidden;
		z-index: 1;
	}

	.contact-card::before {
		content: '';
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background: linear-gradient(135deg, rgba(229, 9, 20, 0.1) 0%, rgba(229, 9, 20, 0) 100%);
		opacity: 0;
		transition: opacity 0.3s ease;
		z-index: -1;
	}

	.contact-card:hover {
		transform: translateY(-5px);
		border-color: var(--primary-color);
		box-shadow: 0 10px 30px rgba(229, 9, 20, 0.2);
	}

	.contact-card:hover::before {
		opacity: 1;
	}

	.card-icon {
		width: 70px;
		height: 70px;
		border-radius: 50%;
		display: flex;
		align-items: center;
		justify-content: center;
		margin-bottom: 1.5rem;
		background: rgba(229, 9, 20, 0.1);
		color: var(--primary-color);
		font-size: 2rem;
		transition: all 0.3s ease;
	}

	.contact-card:hover .card-icon {
		background: var(--primary-color);
		color: white;
		transform: scale(1.1);
	}

	.card-icon svg {
		width: 30px;
		height: 30px;
	}

	.contact-card h3 {
		font-size: 1.5rem;
		margin-bottom: 0.75rem;
		color: var(--text-color);
		font-weight: 600;
	}

	.contact-card p {
		color: var(--text-muted-color);
		margin: 0;
		font-size: 1rem;
		transition: color 0.3s ease;
	}

	.contact-card:hover p {
		color: var(--text-color);
	}

	/* Specific card hover effects */
	.linkedin:hover {
		--primary-color: #0a66c2;
		--border-color: rgba(10, 102, 194, 0.3);
	}

	.instagram:hover {
		--primary-color: #e1306c;
		--border-color: rgba(225, 48, 108, 0.3);
	}

	.email:hover {
		--primary-color: #34a853;
		--border-color: rgba(52, 168, 83, 0.3);
	}

	/* Responsive adjustments */
	@media (max-width: 768px) {
		.contact-cards {
			grid-template-columns: 1fr;
			max-width: 400px;
		}

		.contact-card {
			padding: 2rem 1.5rem;
		}
	}

	@media (min-width: 1200px) {
		.contact-cards {
			grid-template-columns: repeat(3, 1fr);
		}
	}
</style>
