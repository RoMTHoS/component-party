<script setup>
import { ref, computed } from 'vue';
const TRAFFIC_LIGHTS = ['red', 'orange', 'green'];
const lightIndex = ref(0);

const light = computed(() => TRAFFIC_LIGHTS[lightIndex.value]);

function nextLight() {
	if (lightIndex.value + 1 > TRAFFIC_LIGHTS.length - 1) {
		lightIndex.value = 0;
	} else {
		lightIndex.value++;
	}
}
</script>

<template>
	<button @click="nextLight">Next light</button>
	<p>Light is: {{ light }}</p>
	<p>
		You must
		<span v-if="light === 'red'">STOP</span>
		<span v-else-if="light === 'orange'">SLOW DOWN</span>
		<span v-else-if="light === 'green'">GO</span>
	</p>
</template>
