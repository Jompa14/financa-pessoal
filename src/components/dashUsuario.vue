<template lang="html">
    <div class="alinhamento div-pai">

        <div class="painel-resumo">
            <div
                v-for="p, index in painel"
                :key="index"
                :style="{color: '#' + p.cor}"
                class="valores"
            >
                <p>{{p.texto}}</p>
                <p>R$ {{p.valor}}</p>
            </div>
        </div>
        <div class="dashMaisTabela">
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
                            <option value="entrada">Entrada</option>
                            <option value="saída">Saída</option>
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
                            <option value="saúde">Saúde</option>
                            <option value="alimentacao">Alimentação</option>
                            <option value="despesas">Despesas fixas</option>
                            <option value="mimos">Mimos</option>
                            <option value="jobs">Jobs</option>
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

            <div class="box margin-esquerda-desk">
                <h2>Histórico</h2>
                <div
                    v-if="listaTransacoes.length === 0"
                >
                    Você ainda não fez nenhuma transação
                </div>
                <table
                    v-else
                    class="tabela"
                >
                    <thead>
                        <th v-for="(coluna, index) in tabela.colunas" :key="index"> {{coluna}}</th>
                    </thead>
                    <tbody>
                        <tr v-for="(item, index) in listaTransacoes" :key="index">
                            <td>{{item.titulo}}</td>
                            <td
                                :style="item.tipo === 'saída'
                                    ? 'color: #f48d67; font-weight: bold'
                                    : 'color: #3ec8b3; font-weight: bold'"
                            >
                                {{item.tipo}}
                            </td>
                            <td>{{item.categoria}}</td>
                            <td>
                                <span v-if="item.tipo === 'saída'">- </span>
                                {{item.valor}}
                            </td>
                            <td>{{item.data}}</td>
                        </tr>
                    </tbody>
                </table>

            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            painel: [
                {
                    texto: 'Total Entradas:',
                    valor: this.totalEntradas,
                    cor: '3ec8b3',
                },
                {
                    texto: 'Total saídas:',
                    valor: this.totalSaidas,
                    cor: 'f48d67',
                },
                {
                    texto: 'Saldo:',
                    valor: this.saldo,
                    cor: '00a6d8',
                },
            ],
            tabela: {
                colunas: [ 'Título','Tipo', 'Categoria','Valor', 'Data'],
            },
            transacao: {
                titulo: '',
                tipo: '',
                categoria: '',
                valor: 0,
                data: '',
            },
            listaTransacoes: [],
            totalEntradas: 0,
            totalSaidas: 0,
            saldo: 0,
        }
    },
    methods: {
        submeter(objeto) {
            objeto.tipo === 'entrada'
                ? this.totalEntradas += parseInt(objeto.valor)
                : this.totalSaidas += parseInt(objeto.valor)
            this.saldo = this.totalEntradas - this.totalSaidas
            console.log(this.totalSaidas, this.totalEntradas, this.saldo)
            objeto.data = this.retornaData()
            this.listaTransacoes.push({...objeto})
            localStorage.listaTransacoes = this.listaTransacoes
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
        flex-direction: column;
    }
    .painel-resumo {
        border: 1px solid black;
        width: 100%;
        display: flex;
        justify-content: space-around;
        align-items: center;
        .valores {
            padding: 15px 0;
        }
        p {
            font-weight: bold;
            margin: 0;
            font-size: 20px;
        }
        p:nth-child(2) {
            font-size: 25px;
        }
        @media (max-width: 600px) {
            flex-direction: column;
            align-items: flex-start;
            padding: 10px 0;
            p {
                margin-top: 2px;
                margin-bottom: 2px;
            }
            p:nth-child(2) {
                margin-left: 5px;
            }
            .valores {
                margin-left: 16px;
                display: flex;
                align-items: center;
                padding-top: 0;
                padding-bottom: 0;
            }
        }
    }
    .dashMaisTabela {
        display: flex;
        @media (max-width: 600px) {
            flex-direction: column;
        }
    }
    .box {
        display: flex;
        flex-direction: column;
    }
    .margin-esquerda-desk {
        margin-left: 100px;
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
    .tabela {
        border: 1px solid grey;
        border-radius: 4px;
        th {
            padding: 5px 25px;
        }
        th:first-child {
            padding: 5px 155px;
        }
        td:last-child {
            padding: 5px 20px 5px 5px;
        }
        td {
            text-align: center;
            text-transform: capitalize;
        }
    }
</style>
