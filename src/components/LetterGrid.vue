<template>
    <v-sheet class="mx-auto" max-width="400" rounded="xl" border>
        <v-chip-group selected-class="text-primary" multiple column>
            <v-chip  size="x-large" v-for="(tag, tid) in letters" :key="tid">
                <div style="min-width: 12px; text-align: center;">{{ tag.toUpperCase() }} </div>
            </v-chip>
        </v-chip-group>
    </v-sheet>


</template>

<script setup lang="ts">
import { computed } from 'vue';
import LetterCell from './LetterCell.vue';
import { PropType } from 'vue';

const props = defineProps({
    letters: {
        type: Array as PropType<Array<string>>
    }
});

const rows = computed(() => {
    const rows: string[][] = [];
    let row: string[] = [];
    props.letters?.forEach(letter => {
        row.push(letter);
        if (row.length == 6) {
            rows.push(row);
            row = [];
        }
    });
    if (row.length > 0) {
        rows.push(row);
    }
    return rows;
});

</script>

<style lang="css" scoped>
.cell {
    height: 50px;
    width: 50px;
    text-align: center;
    vertical-align: middle;
}
</style>