<script>
	export default {
		name: "TimerCompoment",
		data() {
			return {
				sec: 0,
				min: 0,
				hour: 0,
				timer: null,
				activeColor: '#9E9E9E'
			}
		},
		methods: {
			startTimer() {
				if (!this.timer) {
					this.activeColor = '#ffffff';
					this.timer = setInterval(() => {
						this.sec++;
						if (this.sec === 60) {
							this.sec = 0;
							this.min++
							if (this.min === 60) {
								this.min = 0;
								this.hour++;
							}
						}
					}, 1000)
				}
			},
			pauseTimer() {
				clearTimeout(this.timer)
				this.activeColor = '#9E9E9E';
				this.timer = null;
			},
			clearTimer() {
				this.sec = 0;
				this.min = 0;
				this.hour = 0;
			}
		},
	}
</script>

<template>
	<div class="timer">
		<div class="timer__time" :style="{color: activeColor}">
			{{hour > 0 ? hour + ':' : ''}}{{hour > 0 && min === 0 ? '00' : ''}}{{min > 0 ? (min < 10 && hour > 0 ? '0' : '') + min + ':' : ''}}{{sec < 10 && min > 0 ? '0' + sec : sec}}
		</div>
		<hr :style="{background: activeColor}">
		<div class="timer__btns">
			<svg v-if="!timer" @click="startTimer" width="17" height="20" viewBox="0 0 17 20" fill="none" xmlns="http://www.w3.org/2000/svg">
				<path class="timer__item" :style="{fill: activeColor}" d="M0 20V0L17 10L0 20Z"/>
			</svg>
			<svg v-if="timer" @click="pauseTimer" width="10" height="20" viewBox="0 0 10 20" fill="none" xmlns="http://www.w3.org/2000/svg">
				<rect class="timer__item" :style="{fill: activeColor}" x="7" width="3" height="20"/>
				<rect class="timer__item" :style="{fill: activeColor}" width="3" height="20"/>
			</svg>
			<svg @click="clearTimer" width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
				<rect class="timer__item" :style="{fill: activeColor}" width="20" height="20"/>
			</svg>
		</div>
	</div>
</template>



