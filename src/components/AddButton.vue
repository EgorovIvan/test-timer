<script>
	export default {
		name: "AddButton",
		props: ['addTimer']
	}
</script>

<template>
	<button class="btn-add" @click="addTimer">
		<svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
			<rect class="plus" x="8.5" width="3" height="20" />
			<rect class="plus"  y="11.5" width="3" height="20" transform="rotate(-90 0 11.5)" />
		</svg>
	</button>
</template>


