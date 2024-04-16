<template>
    <section class="representantes">
        <h2>Representantes da 923A</h2>

        <div class="representantes__conteiner">
            <Representante
                v-for="(representante, i) in representantes"
                :key="i"
                :rep="representante"
            />
        </div>
    </section>
</template>

<script>
    import Representante from './Representante.vue'

    export default {
        components: {
            Representante
        },
        data() {
            return {
                representantes: [
                    {
                        imagem: 'https://raw.githubusercontent.com/ethamorim/site-923a/main/public/eu-2023.jpeg',
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
                ],
            }
        }
    }
</script>

