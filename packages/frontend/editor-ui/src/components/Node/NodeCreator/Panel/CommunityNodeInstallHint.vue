<script setup lang="ts">
import { useUsersStore } from '@/stores/users.store';
import { computed } from 'vue';

import { N8nText, N8nIcon } from '@n8n/design-system';

export interface Props {
	hint: string;
}

const isOwner = computed(() => useUsersStore().isInstanceOwner);

defineProps<Props>();
</script>

<template>
	<div v-if="isOwner" :class="$style.container">
		<N8nIcon color="text-light" icon="info" size="large" />
		<N8nText color="text-base" size="medium"> {{ hint }} </N8nText>
	</div>
</template>

<style lang="scss" module>
.container {
	display: flex;
	align-items: center;
	gap: var(--spacing-s);
	margin: var(--spacing-xs);
	margin-top: 0;
	padding: var(--spacing-xs);
	border: var(--border-width-base) solid var(--color-foreground-base);
	border-radius: 0.25em;
	pointer-events: none;
	cursor: default;
}
</style>
