<template lang="html">
    <div class="alinhamento div-pai">
        <div class="box">
            <h2>Dashboard</h2>
            <form
                class="inputs"
                @submit.prevent="submeter(transacao)"
            >
                <div class="inputLabel">
                    <label for="titulo">Título:</label>
                    <input
                        v-model="transacao.titulo"
                        id="titulo"
                        type="text"
                        name="titulo"
                        required
                    />
                </div>
                <div class="inputLabel">
                    <label for="tipo">Tipo:</label>
                    <select
                        v-model="transacao.tipo"
                        id="tipo"
                        name="tipo"
                        required
                        >
                        <option value="valor1">Entrada</option>
                        <option value="valor2">Saída</option>
                    </select>
                </div>
                <div class="inputLabel">
                    <label for="categoria">Categoria:</label>
                    <select
                        v-model="transacao.categoria"
                        id="categoria"
                        name="categoria"
                        required
                    >
                        <option value="1">Saúde</option>
                        <option value="2">Alimentação</option>
                        <option value="3">Despesas fixas</option>
                        <option value="4">Mimos</option>
                        <option value="5">Jobs</option>
                    </select>
                </div>
                <div class="inputLabel">
                    <label for="titulo">Valor:</label>
                    <input
                        v-model="transacao.valor"
                        id="valor"
                        type="number"
                        name="valor"
                        required
                    />
                </div>
                <!-- botao -->
                <input
                    class="btnStyle"
                    type="submit"
                    value="Salvar"
                />
            </form>
        </div>

        <div class="box">
            <h2>Histórico</h2>
            <div class="tabela">
                <div class="headerTabela">

                </div>
                {{listaTransacoes}}
            </div>

        </div>

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
            },
            listaTransacoes: [],
        }
    },
    methods: {
        submeter(objeto) {
            objeto.data = this.retornaData()
            this.listaTransacoes.push({...objeto})
        },
        // famoso metodo para retornar a data
        retornaData () {
            return new Date().toLocaleDateString();
         },
    }
}
</script>

<style lang="scss" scoped>
    .div-pai {
        padding-top: 20px;
        display: flex;
    }
    .box {
        display: flex;
        flex-direction: column;
    }
    .inputs {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        input, label, select {
            margin: 5px;
            margin-left: 0;
            max-width: 200px;
            border-color: #3ec8b3;
            border-radius: 4px;
        }
    }
    .inputLabel {
        display: flex;
        flex-direction: column;
    }
    .btnStyle {
        padding: 10px;
        margin-top: 15px !important;
        background-color: #3ec8b3;
        color: white;
        border-color: #3ec8b3;
        border-radius: 4px;
        font-size: 16px;
        font-weight: bold;
    }
</style>
