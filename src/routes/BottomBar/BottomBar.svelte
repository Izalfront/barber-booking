<script lang="ts">
	import home from './img/home.svg';
	import chat from './img/chat.svg';
	import booking from './img/booking.svg';
	import profile from './img/profil.svg';
	import { goto } from '$app/navigation';

	let activeTab = 'home';

	function handleTabClick(tabName: string) {
		activeTab = tabName;

		// Navigate to different pages based on the tabName
		if (tabName === 'home') goto('/home');
		else if (tabName === 'booking') goto('/booking');
		else if (tabName === 'chat') goto('/home');
		else if (tabName === 'profile') goto('/home');
	}

	const menuItems = [
		{ id: 'home', icon: home, label: 'Home' },
		{ id: 'booking', icon: booking, label: 'Booking' },
		{ id: 'chat', icon: chat, label: 'Chat' },
		{ id: 'profile', icon: profile, label: 'Profile' }
	];
</script>

<div class="border border-t-gray-200 p-6 border-t-2 bg-white">
	<ul class="flex justify-between items-center mx-6">
		{#each menuItems as item}
			<!-- svelte-ignore a11y_click_events_have_key_events -->
			<!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
			<li
				class="flex flex-col items-center space-y-1 cursor-pointer transition-colors duration-200"
				class:active={activeTab === item.id}
				on:click={() => handleTabClick(item.id)}
			>
				<img
					src={item.icon}
					alt="{item.label} Icon"
					class="w-6 h-6"
					class:active-icon={activeTab === item.id}
				/>
				<span class:active-text={activeTab === item.id}>{item.label}</span>
			</li>
		{/each}
	</ul>
</div>

<style>
	.active {
		background-color: transparent;
	}

	.active-text {
		color: #363062;
		font-weight: 600;
	}

	img {
		transition: transform 0.2s ease;
	}

	.active-icon {
		filter: invert(0%) sepia(0%) saturate(0%) hue-rotate(0deg) brightness(0%) contrast(50%);
	}
</style>
