<script setup lang="ts">
defineProps<{
  search?: string
  noPadding?: boolean
}>()

const emit = defineEmits<{
  (event: 'update:search', value: string): void
}>()

function update(event: any) {
  emit('update:search', event.target.value)
}
</script>

<template>
  <div flex="~ col gap2 wrap" border="b base" n-navbar-glass flex-1 :class="[{ p4: !noPadding }]">
    <div flex="~ gap4 wrap" items-center>
      <slot name="search">
        <NTextInput
          v-if="search !== undefined"
          placeholder="Search..."
          icon="carbon-search"
          n="primary" flex-auto
          :class="{ 'px-3 py-2': !noPadding }"
          :value="search"
          @input="update"
        />
      </slot>
      <slot name="actions" />
    </div>
    <slot />
  </div>
</template>
