<template>
    <main class="home">
        <section class="destaque">
            <h2>As fardas do 3° ano nunca estiveram tão perto!</h2>

            <div class="fardas">
                <img
                class="frente"
                src="@/assets/imgs/farda-casual-frente.png"
                alt="Frente da farda casual do curso de Desenvolvimento de Sistemas" />
                <img
                class="verso"
                src="@/assets/imgs/farda-casual-verso.png"
                alt="Verso da farda casual do curso de Desenvolvimento de Sistemas" />
            </div>

            <p>Confira os designs escolhidos pelas turmas do curso:</p>
            <div class="opcoes-fardas">
                <button class="ativa">Casual</button>
                <button>Polo</button>
            </div>
        </section>

        <section class="pedido">
            <h3>Faça seu pedido pelo forms!</h3>
            <p class="obs">
                Pague metade do preço até o dia 20 de agosto
                e pague o restante apenas quando receber as fardas
            </p>

            <a class="botao-forms" href="#">Forms</a>
        </section>

        <section class="avisos">
            <h2>Avisos</h2>

            <div class="cards">
                <CardAviso v-for="i in [1, 2, 3]" :key="i" />
            </div>

            <button class="ver-mais-avisos">Ver mais</button>
        </section>

        <section class="horarios">
            <h2>Horários de aula</h2>
            <p>Os horários ainda não estão disponíveis. Em breve serão disponibilizados nessa seção.</p>
        </section>
    </main>

    <section class="representantes">
        <h2>Representantes da 923A</h2>

        <Representante
            v-for="(representante, i) in representantes"
            :key="i"
            :rep="representante"
        />
    </section>
</template>

<script>
    import CardAviso from '@/components/CardAviso.vue';
    import Representante from '@/components/Representante.vue';

    export default {
        components: {
            CardAviso,
            Representante,
        },
        data() {
            return {
                representantes: [
                    {
                        imagem: 'https://user-images.githubusercontent.com/87045182/180874614-8191bd44-3aa1-437a-ac75-7bc3c6a97dd7.jpeg',
                        altImagem: 'foto de Ytalo dos Santos Amorim, representante da 923A',
                        bandeira: 'bandeira-gay',
                        nome: 'Ytalo',
                        apelido: 'Ethan',
                        sobrenome: 'Amorim',
                        titulo: 'representante',
                        sobre: 'ele/dele. viciado em programar. não vai resolver muita coisa pra você, mas vai tentar',
                        telefone: '(82) 998289990',
                        email: 'ysa4@aluno.ifal.edu.br'
                    },
                    {
                        imagem: 'https://user-images.githubusercontent.com/87045182/180874685-7ae7ab72-698d-41fc-90d6-ffb6cd7a8780.jpeg',
                        altImagem: 'foto de Alexia Rodrigues, vice-representante da 923A',
                        bandeira: 'bandeira-bi',
                        nome: 'Alexia',
                        apelido: 'Alê',
                        sobrenome: 'Rodrigues',
                        titulo: 'vice-representante',
                        sobre: 'ela/dela. faz mais do que o próprio representante. competente e tem um ótimo papo',
                        telefone: '(82) 988782195',
                        email: 'arso1@aluno.ifal.edu.br'
                    }
                ]
            }
        }
    }

</script>
