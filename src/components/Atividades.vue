<template>
    <section id="atividades" class="atividades">
        <h2>Atividades</h2>

        <div class="cards">
            <CardAtividade v-for="i in [1, 2, 3]" :key="i" />
        </div>

        <button class="ver-mais-atividades">Ver mais</button>
    </section>
</template>

<script>
    import CardAtividade from './CardAtividade.vue'

    export default {
        components: {
            CardAtividade
        }
    }
</script>
