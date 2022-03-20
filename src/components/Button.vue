<script lang="ts" setup>
defineProps({
    text: String,
    fontColor: String,
    bgColor: String,
})

defineEmits([
    'emitted-click'
])
</script>

<template>
    <button
        @click="$emit('emitted-click')"
        :style="{ 'color': `${fontColor}`, 'background-color': `${bgColor}` }"
        type="button"
    >{{ text }}</button>
</template>

<style scoped>
button {
    padding: 4px 8px;
    background-color: #ffffff;
    color: green;
    border: none;
    outline: none;
    border-radius: 4px;
    box-shadow: 0px 2px 4px 0px #80808087;
    width: fit-content;
    height: 36px;
    cursor: pointer;
}
</style>
