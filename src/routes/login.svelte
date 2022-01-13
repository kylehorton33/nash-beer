<script>
	let username,
		password = '';

	let errors = [];

	const handleLogin = () => {
		console.log(username, password);

		errors = [];

		if (username != 'testuser') {
			errors = ['There is no user with that name', ...errors];
		}

		if (username != 'testpassword') {
			errors = ['Incorrect Password', ...errors];
		}
	};
</script>

<div class="flex flex-row justify-center mt-8 mb-16">
	<div class="card shadow-2xl lg:card-side bg-base-300 w-96">
		<div class="card-body">
			<form on:submit|preventDefault={handleLogin}>
				<div class="form-control">
					{#each errors as error}
						<div class="alert alert-error mb-2">{error}</div>
					{/each}
					<label class="label">
						<span class="label-text">Username</span>
					</label>
					<input
						bind:value={username}
						placeholder="user@example.com"
						class="input input-bordered"
						type="text"
					/>
					<label class="label">
						<span class="label-text">Password</span>
					</label>
					<input
						bind:value={password}
						placeholder="password"
						class="input input-bordered"
						type="password"
					/>
					<div class="login-placeholder h-20" />
				</div>

				<div class="justify-end card-actions mt-7">
					<button class="btn btn-primary" on:click={handleLogin}> Login </button>
				</div>
			</form>
			<div class="flex flex-row justify-center mt-6">
				<a href="/signup" class="label-text-alt" data-bcup-haslogintext="no"
					>Need a new account? Sign up here.</a
				>
			</div>
		</div>
	</div>
</div>
