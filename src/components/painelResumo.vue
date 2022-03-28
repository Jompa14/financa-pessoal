<template lang="html">
    <div>
        <div class="div-pai">
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
    </div>
</template>

<script>
export default {
    props: {
        totalEntradas: {
            default: 0,
            type: Number,
        },
        totalSaidas: {
            default: 0,
            type: Number,
        },
        saldo: {
            default: 0,
            type: Number,
        },
    },
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
        }
    }
}
</script>

<style lang="scss" scoped>
    .div-pai {
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
</style>
