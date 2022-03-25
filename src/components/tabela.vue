<template lang="html">
    <div class="">
        <img :src="{{mdiAlienOutline}}" alt="alienzinho">
        <p>{{ teste }}</p>
    </div>
</template>

<script>
import { mdiAlienOutline } from '@mdi/js';
export default {
    data() {
        mdiAlienOutline,
        teste: 'oizinho',
    }
}
</script>

<style lang="css" scoped>
</style>
