<template>
    <section class="destaque">
        <div class="destaque__titulo">
            <h2>As fardas do 3° ano nunca estiveram tão perto!</h2>
        </div>

        <div class="fardas-conteiner">
            <Fardas
                :class="(fardaAtiva === 'casual') ? 'uniforme-entrando' : ''"
                v-show="fardaAtiva === 'casual'"
                :farda="fardas.casual"
            />
            <Fardas
                :class="(fardaAtiva === 'polo') ? 'uniforme-entrando' : ''"
                v-show="fardaAtiva === 'polo'"
                :farda="fardas.polo"
            />

            <div class="conferir-designs">
                <p>Confira os designs escolhidos pelas turmas do curso:</p>

                <div class="opcoes-fardas">
                    <button
                        :class="(fardaAtiva === 'casual') ? 'ativa' : ''"
                        @click.prevent="setFarda('casual')">
                        Casual
                    </button>
                    <button
                        :class="(fardaAtiva === 'polo') ? 'ativa' : ''"
                        @click.prevent="setFarda('polo')">
                        Polo
                    </button>
                </div>
            </div>
        </div>
    </section>

    <section class="caminho">
        <h3>Elas estão a caminho!</h3>
        <p>
            Os pedidos já foram confirmados e as fardas estão finalmente sendo produzidas.
        </p>

        <p class="obs">
            Para mais informações contate a vice-representante Alexia
        </p>
    </section>
</template>

<script>
    import Fardas from './Fardas.vue'

    export default {
        components: {
            Fardas
        },
        data() {
            return {
                fardas: {
                    casual: {
                        nome: 'casual',
                        frente: 'https://user-images.githubusercontent.com/87045182/180905631-04446bb4-96d4-4efc-8bde-903821eb45b5.png',
                        verso: 'https://user-images.githubusercontent.com/87045182/180905635-2d0b7b6c-f008-438e-b6df-154b8213097c.png'
                    },
                    polo: {
                        nome: 'polo',
                        frente: 'https://user-images.githubusercontent.com/87045182/180905664-aefc439c-c2a4-4366-b26f-55aa14951626.png',
                        verso: 'https://user-images.githubusercontent.com/87045182/180905671-5db2f6ee-b144-472b-bdff-d0471664b125.png'
                    }
                },
                fardaAtiva: 'casual'
            }
        },
        methods: {
            setFarda(nome) {
                this.fardaAtiva = nome;
            }
        }
    }
</script>
