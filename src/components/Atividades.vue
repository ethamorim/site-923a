<template>
    <section id="atividades" class="atividades">
        <div class="atividades__header">
            <h2>Atividades</h2>
            <i class="material-icons-round" @click.left="abrirModalAdicionarAtividades">
                library_add
            </i>
        </div>

        <div class="cards">
            <p class="sem-atividades" v-if="!atividades.length">
                <em>Ufa! Não há atividades cadastradas.</em>
            </p>

            <CardAtividade v-for="ativ in atividades" :key="ativ.id" />
        </div>

        <button class="ver-mais-atividades">Ver mais</button>
    </section>

    <AdicionarAtividades
        v-if="modalAdicionarAtividadesAberto"
        @fecharModal="fecharModalAdicionarAtividades"
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
        data() {
            return {
                atividades: [],
                modalAdicionarAtividadesAberto: false,
            }
        },
        methods: {
            abrirModalAdicionarAtividades() {
                this.modalAdicionarAtividadesAberto = true;
            },
            fecharModalAdicionarAtividades() {
                this.modalAdicionarAtividadesAberto = false;
            }
        },
        beforeMount() {
            axios.get('https://ws-site-923a.herokuapp.com/atividades')
                .then((promise) => {
                    this.atividades = promise.data;
                });
        }
    }
</script>
