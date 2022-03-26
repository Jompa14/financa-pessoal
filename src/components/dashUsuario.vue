<template lang="html">
    <div class="alinhamento div-pai">
        <h2>Dashboard</h2>
        <label for="titulo">Título:</label>
        <input
            v-model="transacao.titulo"
            id="titulo"
            type="text"
            name="titulo"
        />
    </div>
</template>

<script>
export default {
    data() {
        return {
            transacao: {
                titulo: '',
                tipo: '',
                categoria: '',
                valor: 0,
                data: '',
            }
        }
    }
}
</script>

<style lang="scss" scoped>
    .div-pai {
        padding-top: 20px;
    }
</style>
