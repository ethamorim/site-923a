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

        <Representante />
    </section>
</template>

<script>
    import CardAviso from '@/components/CardAviso.vue';
    import Representante from '@/components/Representante.vue';

    export default {
        components: {
            CardAviso,
            Representante,
        }
    }

</script>
