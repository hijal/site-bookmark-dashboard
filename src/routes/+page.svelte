<script>
	import Payout from '../lib/component/Payout.svelte';
	import Shop from '../lib/component/Shop.svelte';
	import TopUp from '../lib/component/TopUp.svelte';

	let isOpenSidebar = false;

	let activeComponent = Payout;

	function selectComponent(component, isCloseSide = false) {
		activeComponent = component;
		isOpenSidebar = isCloseSide;
	}

	function closeSidebar() {
		isOpenSidebar = false;
	}

	function openSidebar() {
		isOpenSidebar = true;
	}
</script>

<div class="">
	<!-- mobile sidebar -->
	<div
		class="inset-0 lg:hidden fixed z-40 {isOpenSidebar ? 'flex' : 'hidden'}"
		role="dialog"
		aria-modal="true"
	>
		<button
			on:click={closeSidebar}
			class="fixed inset-0 bg-gray-600 bg-opacity-75"
			aria-hidden="true"
		></button>

		<div class="relative flex-1 flex flex-col max-w-xs w-full bg-primary container">
			<div class="absolute top-0 right-0 -mr-12 pt-2">
				<button
					type="button"
					on:click={closeSidebar}
					class="ml-1 flex items-center justify-center h-10 w-10 rounded-full focus:outline-none focus:ring-2 focus:ring-inset focus:ring-white"
				>
					<span class="sr-only">Close sidebar</span>
					<svg
						class="h-6 w-6 text-white"
						xmlns="http://www.w3.org/2000/svg"
						fill="none"
						viewBox="0 0 24 24"
						stroke="currentColor"
						aria-hidden="true"
					>
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M6 18L18 6M6 6l12 12"
						/>
					</svg>
				</button>
			</div>

			<div class="flex-1 h-0 pt-5 pb-4 overflow-y-auto">
				<div class="flex px-4">
					<img class="h-14" src="/images/Logotype.svg" alt="triple-a" />
				</div>
				<nav class="mt-20 flex px-2 space-y-1 w-full flex-col justify-center">
					<button
						on:click={() => selectComponent(Payout)}
						class="hover:bg-navbar hover:bg-opacity-75 group flex items-center px-2 py-2 text-base font-medium rounded-md {activeComponent !==
						Payout
							? 'text-white'
							: ''} {activeComponent === Payout ? 'active-component' : ''}"
					>
						<svg
							xmlns="http://www.w3.org/2000/svg"
							fill="none"
							viewBox="0 0 24 24"
							stroke-width="1.5"
							stroke="currentColor"
							class="mr-3 flex-shrink-0 h-6 w-6 {activeComponent === Payout
								? 'text-primary'
								: 'text-white'}"
						>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								d="M13.19 8.688a4.5 4.5 0 0 1 1.242 7.244l-4.5 4.5a4.5 4.5 0 0 1-6.364-6.364l1.757-1.757m13.35-.622 1.757-1.757a4.5 4.5 0 0 0-6.364-6.364l-4.5 4.5a4.5 4.5 0 0 0 1.242 7.244"
							/>
						</svg>

						Payout Demo
					</button>
					<button
						on:click={() => selectComponent(Shop)}
						class="hover:bg-navbar hover:bg-opacity-75 group flex items-center px-2 py-2 text-base font-medium rounded-md {activeComponent !==
						Shop
							? 'text-white'
							: ''} {activeComponent === Shop ? 'active-component' : ''}"
					>
						<svg
							xmlns="http://www.w3.org/2000/svg"
							fill="none"
							viewBox="0 0 24 24"
							stroke-width="1.5"
							stroke="currentColor"
							class="mr-3 flex-shrink-0 h-6 w-6 {activeComponent === Shop
								? 'text-primary'
								: 'text-white'}"
						>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								d="M13.19 8.688a4.5 4.5 0 0 1 1.242 7.244l-4.5 4.5a4.5 4.5 0 0 1-6.364-6.364l1.757-1.757m13.35-.622 1.757-1.757a4.5 4.5 0 0 0-6.364-6.364l-4.5 4.5a4.5 4.5 0 0 0 1.242 7.244"
							/>
						</svg>

						Shop Demo
					</button>
					<button
						on:click={() => selectComponent(TopUp)}
						class="hover:bg-navbar hover:bg-opacity-75 group flex items-center px-2 py-2 text-base font-medium rounded-md {activeComponent !==
						TopUp
							? 'text-white'
							: ''} {activeComponent === TopUp ? 'active-component' : ''}"
					>
						<svg
							xmlns="http://www.w3.org/2000/svg"
							fill="none"
							viewBox="0 0 24 24"
							stroke-width="1.5"
							stroke="currentColor"
							class="mr-3 flex-shrink-0 h-6 w-6 {activeComponent === TopUp
								? 'text-primary'
								: 'text-white'}"
						>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								d="M13.19 8.688a4.5 4.5 0 0 1 1.242 7.244l-4.5 4.5a4.5 4.5 0 0 1-6.364-6.364l1.757-1.757m13.35-.622 1.757-1.757a4.5 4.5 0 0 0-6.364-6.364l-4.5 4.5a4.5 4.5 0 0 0 1.242 7.244"
							/>
						</svg>

						Top-up Demo
					</button>
				</nav>
			</div>
		</div>
	</div>

	<!-- desktop sidebar -->
	<div class="hidden md:flex md:w-64 md:flex-col md:fixed md:inset-y-0">
		<div class="flex-1 flex flex-col min-h-0 bg-primary">
			<div class="flex-1 flex flex-col pt-5 pb-4 overflow-y-auto">
				<a href="/" class="flex items-center justify-center">
					<img class="h-14 w-10/12" src="/images/Logotype.svg" alt="triple-a" />
				</a>
				<nav class="mt-20 space-y-1.5 flex justify-center flex-col">
					<button
						on:click={() => selectComponent(Payout)}
						class="hover:bg-navbar hover:bg-opacity-75 group flex items-center px-2 py-2 text-base font-medium rounded-md {activeComponent !==
						Payout
							? 'text-white'
							: ''} {activeComponent === Payout ? 'active-component' : ''}"
					>
						<svg
							xmlns="http://www.w3.org/2000/svg"
							fill="none"
							viewBox="0 0 24 24"
							stroke-width="1.5"
							stroke="currentColor"
							class="mr-3 flex-shrink-0 h-6 w-6 {activeComponent === Payout
								? 'text-primary'
								: 'text-white'}"
						>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								d="M13.19 8.688a4.5 4.5 0 0 1 1.242 7.244l-4.5 4.5a4.5 4.5 0 0 1-6.364-6.364l1.757-1.757m13.35-.622 1.757-1.757a4.5 4.5 0 0 0-6.364-6.364l-4.5 4.5a4.5 4.5 0 0 0 1.242 7.244"
							/>
						</svg>

						Payout Demo
					</button>
					<button
						on:click={() => selectComponent(Shop)}
						class="hover:bg-navbar hover:bg-opacity-75 group flex items-center px-2 py-2 text-base font-medium rounded-md {activeComponent !==
						Shop
							? 'text-white'
							: ''} {activeComponent === Shop ? 'active-component' : ''}"
					>
						<svg
							xmlns="http://www.w3.org/2000/svg"
							fill="none"
							viewBox="0 0 24 24"
							stroke-width="1.5"
							stroke="currentColor"
							class="mr-3 flex-shrink-0 h-6 w-6 {activeComponent === Shop
								? 'text-primary'
								: 'text-white'}"
						>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								d="M13.19 8.688a4.5 4.5 0 0 1 1.242 7.244l-4.5 4.5a4.5 4.5 0 0 1-6.364-6.364l1.757-1.757m13.35-.622 1.757-1.757a4.5 4.5 0 0 0-6.364-6.364l-4.5 4.5a4.5 4.5 0 0 0 1.242 7.244"
							/>
						</svg>

						Shop Demo
					</button>
					<button
						on:click={() => selectComponent(TopUp)}
						class="hover:bg-navbar hover:bg-opacity-75 group flex items-center px-2 py-2 text-base font-medium rounded-md {activeComponent !==
						TopUp
							? 'text-white'
							: ''} {activeComponent === TopUp ? 'active-component' : ''}"
					>
						<svg
							xmlns="http://www.w3.org/2000/svg"
							fill="none"
							viewBox="0 0 24 24"
							stroke-width="1.5"
							stroke="currentColor"
							class="mr-3 flex-shrink-0 h-6 w-6 {activeComponent === TopUp
								? 'text-primary'
								: 'text-white'}"
						>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								d="M13.19 8.688a4.5 4.5 0 0 1 1.242 7.244l-4.5 4.5a4.5 4.5 0 0 1-6.364-6.364l1.757-1.757m13.35-.622 1.757-1.757a4.5 4.5 0 0 0-6.364-6.364l-4.5 4.5a4.5 4.5 0 0 0 1.242 7.244"
							/>
						</svg>

						Top-up Demo
					</button>
				</nav>
			</div>
		</div>
	</div>
	<div class="md:pl-64 flex flex-col justify-center flex-1 h-16">
		<div
			class="sticky top-0 z-10 md:hidden pl-1 pt-0 sm:pl-3 sm:pt-3 bg-primary flex justify-between items-center"
		>
			<a href="/" class="flex">
				<img class="h-12 w-10/12" src="/images/Logotype.svg" alt="triple-a" />
			</a>
			<button
				on:click={openSidebar}
				type="button"
				class="-ml-0.5 h-16 w-16 inline-flex items-center justify-center rounded-md text-gray-500 hover:text-gray-900 focus:outline-none"
			>
				<span class="sr-only">Open sidebar</span>
				<svg
					class="h-7 w-7 text-white mt-0"
					xmlns="http://www.w3.org/2000/svg"
					fill="none"
					viewBox="0 0 24 24"
					stroke="currentColor"
					aria-hidden="true"
				>
					<path
						stroke-linecap="round"
						stroke-linejoin="round"
						stroke-width="2"
						d="M4 6h16M4 12h16M4 18h16"
					/>
				</svg>
			</button>
		</div>
		<!-- content -->
		<main class="flex-1">
			<div class="py-6">
				<div class="max-w-7xl px-5 sm:px-7 flex sm:justify-center lg:pt-44 pt-56">
					<svelte:component this={activeComponent}></svelte:component>
				</div>
			</div>
		</main>
	</div>
</div>
