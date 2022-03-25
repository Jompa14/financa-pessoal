<template lang="html">
    <div class="">
        <p>oioioi</p>
        <img src="mdiAlienOutline" alt="alienzinho">
        <p>{{ teste }}</p>
    </div>
</template>

<script>
export default {
    name: 'tabela-usuario',
    data: function() {
        return {
            teste: 'oizinho',
        }
    }
}
</script>

<style lang="scss" scoped>
p {
    color: purple;
}
</style>
