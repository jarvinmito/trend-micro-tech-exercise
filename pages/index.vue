<template>
	<section class="main">
		<div class="signup">
			<a href="#" class="signup__nav dark">
				<img src="/arrow.svg" />
				Back
			</a>
			<div class="signup__container">
				<div>
					<h2>Start from free</h2>
					<h1>Create an account</h1>
				</div>
				<div class="signup__socmed">
					<button class="icon light">
						<div>
							<svg width="22" height="22" viewBox="0 0 22 22" fill="none" xmlns="http://www.w3.org/2000/svg">
								<path d="M11 8.8V13.2H17.2238C16.3152 15.7608 13.8688 17.6 11 17.6C7.3612 17.6 4.4 14.6388 4.4 11C4.4 7.3612 7.3612 4.4 11 4.4C12.5774 4.4 14.0954 4.9654 15.2746 5.9928L18.1654 2.6752C16.1854 0.9504 13.6422 0 11 0C4.9346 0 0 4.9346 0 11C0 17.0654 4.9346 22 11 22C17.0654 22 22 17.0654 22 11V8.8H11Z" fill="#3C71FF"/>
							</svg>
							<!-- <img src="/google.svg" /> -->
						</div>
						Sign up with Google
					</button>
					<button class="icon light">
						<div>
							<svg width="12" height="22" viewBox="0 0 12 22" fill="none" xmlns="http://www.w3.org/2000/svg">
								<path d="M9.66391 3.65292H11.6723V0.154917C11.3258 0.10725 10.1342 0 8.74633 0C5.85058 0 3.86692 1.82142 3.86692 5.16908V8.25H0.671416V12.1605H3.86692V22H7.78475V12.1614H10.851L11.3377 8.25092H7.78383V5.55683C7.78475 4.42658 8.08908 3.65292 9.66391 3.65292Z" fill="#3C71FF"/>
							</svg>
							<!-- <img src="/facebook.svg" /> -->
						</div>
						Sign up with Facebook
					</button>
				</div>
				<div class="signup__separator">
					<p>Or use your email for registration</p>
					<hr />
				</div>
				<div class="signup__personal">
					<TextInput v-model="first_name" label="First Name" />
					<TextInput v-model="last_name" label="Last Name" />
				</div>
				<TextInput v-model="email" label="Email" />
				<PasswordInput v-model="password" label="Password" />
				<!-- <TextInput v-model="password" label="Password" /> -->
				<div class="signup__terms">
					<CheckInput v-model="agreed" class="signup__terms__check" />
					<p class="sub">By creating account, you agree to accept our Privacy Policy, Terms of Service and Notification settings.</p>
				</div>
				<button class="signup__action" @click="signUp">Create an Free Account!</button>
				<p class="sub signup__link">Already have an account? <a href="#">Login</a></p>
			</div>
		</div>
	</section>
</template>

<script>
export default {
	methods: {
		signUp () {
			console.log('SignUp triggered!!')
		}
	},
	data () {
		return {
			first_name: '',
			last_name: '',
			email: '',
			password: '',
			agreed: false
		}
	}
}
</script>

<style lang="scss">
:root {
	--font-size: 10px;
	--color-white: #ffffff;
	--color-black: #000000;
	--color-gray-light: #F1F5FF;
	--color-gray-shadow: #e4e6eb;
	--color-gray: #ababab;
	--color-gray-dark: #757575;
	--color-accent: #3C71FF;
	--color-accent-light: #90aaf2;
}
html, body {
	font-family: 'Lato', sans-serif;
	font-size: var(--font-size);
	background-color: var(--color-gray-light);
}

* {
	box-sizing: border-box;
	padding: 0;
	margin: 0;
}

// titles
h1 {
	font-size: 3rem;
	font-weight: 700;
	margin: 0;
	margin-bottom: 0.4rem;
}
// subtitles
h2 {
	font-size: 1.8rem;
	font-weight: 400;
	margin: 0;
	margin-bottom: 0.5rem;
}

p {
	font-size: 1.4rem;
	font-weight: 400;
	margin: 0;
	color: var(--color-black);

	&.sub {
		font-size: 1.3rem;
		color: var(--color-gray-dark);
	}
}

a {
	font-weight: 700;
	font-size: 1.3rem;
	color: var(--color-accent);
	text-decoration: none;

	&.dark {
		color: var(--color-black);
	}
}

button {
	background-color: var(--color-accent);
	color: var(--color-white);
	height: 5.5rem;
	width: 100%;
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
	border: 0.2rem solid var(--color-accent);
	border-radius: 0.5rem;
	cursor: pointer;
	font-size: 1.4rem;
	padding: 1rem;
	transition: all 0.2s ease-in-out;

	&:hover {
		box-shadow: 0 0.4rem 1rem 0 var(--color-accent-light);
	}

	&.light {
		background: transparent;
		border-color: var(--color-accent-light);
		color: var(--color-black);

		&:hover {
			background: var(--color-accent);
			border-color: var(--color-accent);
			color: var(--color-white);
			box-shadow: 0 0.3rem 0.5rem 0 var(--color-gray-shadow);
		}
	}

	&.icon {
		flex-direction: row;
		justify-content: flex-start;
		gap: 1.5rem;
		font-size: 1.3rem;

		& > div {
			height: 2.2rem;
			width: 2.2rem;
			color: var(--color-accent);
			& > svg {
				&,
				& > path {
					fill: currentColor;
					margin: auto;
				}
			}
		}

		&:hover {
			& > div {
				color: var(--color-white);
			}
		}
	}
}

hr {
	border: none;
	border-top: 1px solid var(--color-black);
	min-width: 2rem;
	flex-grow: 1;
}



// Page specific styles
.signup {
	background-color: var(--color-white);
	&__nav,
	&__container {
		display: flex;
		justify-content: flex-start;
		gap: 1.2rem;
		padding: 2rem;
	}
	&__nav {
		flex-direction: row;
		align-items: center;
	}
	&__container {
		flex-direction: column;
		align-items: stretch;
	}

	&__separator,
	&__terms {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		gap: 1.5rem;
	}

	&__terms {
		& > input {
			background: var(--color-gray);
			margin-right: 0.5rem;
		}
		&__check {
			flex-shrink: 0;
		}
	}

	&__link {
		text-align: center;
	}

	&__personal,
	&__socmed {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		gap: 1.2rem;
	}

	&__action {
		margin-top: 1.1rem;
	}
}

// larger screens
@media screen and (min-width: 575px) {
	.main {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		min-height: 100vh;
		width: 100%;
		padding: 6rem;
	}
	.signup {
		border-radius: 2rem;
		box-shadow: 0 0.5rem 1rem 0.5rem var(--color-gray-shadow);
		max-width: 61rem;
		&__container {
			padding: 2rem 10.05rem 3.6rem 10.05rem;
		}
	}
}
</style>