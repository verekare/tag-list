<template>
    <v-container fluid :class="[isHalfWidth && 'mx-0 half-width']">
        <v-row :class="[isStretched ? 'justify-space-between align-center' : 'justify-start align-center']">
            <v-col 
            v-for="(tag, index) in separatedTags"
            :key="index"
            class="flex-grow-0"
            :class="[isHalfWidth ? 
                    'hidden-sm-and-down' : 
                    'justify-center text-no-wrap d-none d-sm-flex']"
            xs="12"
            >
                <v-icon v-if="tag.icon"> {{ tag.icon }}</v-icon>
                <span class="text-no-wrap" v-if="tag.text"> {{ tag.text }}</span>
            </v-col>
        </v-row>
    </v-container>
</template>
<script>
import { mdiCircleSmall } from "@mdi/js";
export default {
    name: 'TagList',
    props: {
        tags: {
            type: Array,
            required: true
        },
        isHalfWidth: {
            type: Boolean,
            required: false
        },
        isStretched: {
            type: Boolean,
            required: false
        }
    },
    computed: {
        separatedTags() { 
            return this.$props.tags.reduce((acc, curr, index, arr) => {
                if (index < arr.length - 1) {
                    return [...acc, curr, {icon: mdiCircleSmall}]
                } else {
                    return [...acc, curr]
                }
            }, [])
        }
    }
}
</script>
<style lang="scss">
.half-width {
    width: 50%;
}
.text-no-wrap {
    white-space: nowrap;
}
</style>