<script setup lang="ts">
import {onUnmounted, Ref, ref} from "vue";

const play: Ref<Boolean> = ref(true)

const player: Ref<HTMLVideoElement> = ref()

const playHandler = () => {
  play.value = !play.value
  if (play.value) {
    player.value.pause()
  } else {
    player.value.play()
  }
}
let interval: ReturnType<typeof setInterval>;
const playerCurrentTime = ref(player?.value?.currentTime ?? 0)
const playerDuration = ref(player?.value?.duration ?? 0)

const loadHandler = () => {
  playerCurrentTime.value = player.value.currentTime;
  playerDuration.value = player.value.duration;

  interval = setInterval(() => {
    playerCurrentTime.value = player.value.currentTime
  }, 1000)
}

onUnmounted(() => {
  clearInterval(interval)
})

</script>

<template>
  <div class="video">
    <video src="../assets/bunny.mp4" width="520px" ref="player" @loadeddata="loadHandler">
    </video>
    <p>{{ playerCurrentTime }} / {{ playerDuration }}</p>
    <div class="btn-container">
      <button @click="playHandler">
        {{ play ? 'Play' : 'Pause' }}
      </button>
    </div>
  </div>

</template>

<style scoped>
.video {
  height: 25%;
  width: 25%;
}
</style>