<template>
    <section id="atividades" class="atividades">
        <div class="atividades__header">
            <h2>Atividades</h2>
            <i class="material-icons-round" @click.left="abrirModalAdicionarAtividades">
                add
            </i>
        </div>

        <div class="cards">
            <div class="cards-to-left">
                <p class="sem-atividades" v-if="!atividades.length">
                    <em>Ufa! Não há atividades cadastradas.</em>
                </p>

                <CardAtividade
                    v-for="ativ in arrAtividades"
                    :key="ativ.id"
                    :atividade="ativ"
                    @getAtividades="getAtividades"
                />
            </div>
        </div>

        <button
            class="ver-mais-atividades"
            @click.prevent="abrirMaisAtividades"
            v-if="!verMais && atividades.length > 3">
            Ver mais
        </button>
        <button
            class="ver-mais-atividades"
            @click.prevent="fecharMaisAtividades"
            v-if="verMais">
            Ver menos
        </button>
    </section>

    <AdicionarAtividades
        v-if="modalAdicionarAtividadesAberto"
        @fecharModal="fecharModalAdicionarAtividades"
        @reload="getAtividades"
    />
</template>

<script>
    import CardAtividade from './CardAtividade.vue';
    import AdicionarAtividades from './modais/AdicionarAtividades.vue';
    const axios = require('axios').default;

    export default {
        components: {
            CardAtividade,
            AdicionarAtividades
        },
        computed: {
            arrAtividades() {
                return this.getArrayDeAtividades();
            }
        },
        data() {
            return {
                atividades: [],
                modalAdicionarAtividadesAberto: false,
                verMais: false,
            }
        },
        methods: {
            abrirModalAdicionarAtividades() {
                this.modalAdicionarAtividadesAberto = true;
            },
            fecharModalAdicionarAtividades() {
                this.modalAdicionarAtividadesAberto = false;
            },
            getAtividades() {
                axios.get('https://ws-site-923a.herokuapp.com/atividades')
                    .then((promise) => {
                        this.atividades = promise.data;
                    });
            },
            getArrayDeAtividades() {
                if (!this.verMais) {
                    return this.atividades.slice(0,3);
                } else {
                    return this.atividades;
                }
            },
            abrirMaisAtividades() {
                this.verMais = true;
            },
            fecharMaisAtividades() {
                this.verMais = false;
            }
        },
        beforeMount() {
            this.getAtividades();
        }
    }
</script>
