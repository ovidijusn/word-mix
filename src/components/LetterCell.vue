<template>
    <div class="cell">{{ value }}</div>
</template>

<script setup lang="ts">
defineProps({
    value: {
        type: String
    }
})
</script>

<style lang="css" scoped>
.cell {
    font-size: 24px;
    font-weight: 900;
    height: 50px;
    width: 50px;
    text-align: center;
    vertical-align: middle;
    display: table-cell;
}
</style>