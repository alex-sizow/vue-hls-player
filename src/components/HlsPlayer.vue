<script setup lang="ts">
import { onMounted, ref } from 'vue';

import Hls from 'hls.js';

defineProps<{ videoUrl: string }>();

onMounted(() => {
	let hls = new Hls();
	let stream = '../assets/master.m3u8';
	let video = ref(null);
	hls.loadSource(stream);
	hls.attachMedia(video);
	hls.on(Hls.Events.MANIFEST_PARSED, function () {
		video.play();
	});
});
</script>

<template>
	<video
		ref="video"
		controls
		src=""></video>
</template>

<style scoped>
.read-the-docs {
	color: #888;
}
</style>
