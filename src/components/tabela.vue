<template lang="html">
    <div class="">
        <p>oioioi</p>
        <img :src="{{mdiAlienOutline}}" alt="alienzinho">
        <p>{{ teste }}</p>
    </div>
</template>

<script>
import { mdiAlienOutline } from '@mdi/js';
export default {
    name: 'tabela';
    data: function() {
        return {
            mdiAlienOutline,
            teste: 'oizinho',
        }
    }
}
</script>

<style lang="css" scoped>
</style>
