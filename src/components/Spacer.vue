<script lang="ts" setup>
type Props = {
  top?: number,
  left?: number,
  right?: number,
  bottom?: number
}

withDefaults(defineProps<Props>(), {
  top: 0,
  left: 0,
  right: 0,
  bottom: 0
})
</script>

<template>
  <div
    :style="{ 'margin': `${top}px ${right}px ${bottom}px ${left}px` }"
  ></div>
</template>
