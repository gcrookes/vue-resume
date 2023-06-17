<template>
	<a :href="link" target="_blank" class="no-decoration">
		<q-card class="row q-pr-sm">
		<div class="rounded-div">
			<div class="bg-accent q-ma-sm rounded-div">
				<q-icon v-if="icon" :name="icon" size="2.5rem" color="black"/>
				<slot />
			</div>
		</div>
		<div class="q-my-auto">
			<div class="text-body text-weight-bold">
			{{ title }}
			</div>
			<div class="text-body2">
			{{ text }}
			</div>
		</div>
		</q-card>
	</a>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'ContactCard',
  props: {
	link: { type: String, default: '' },
    title: { type: String, default: '' },
	text: { type: String, default: '' },
	icon: { type: String, default: '' },
  }
})
</script>

<style lang="sass">
.rounded-div
  border-radius: 5px 5px 5px 5px
</style>