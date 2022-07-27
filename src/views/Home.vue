<template>
    <main id="home" class="home">
        <Destaque />

        <Atividades />

        <Horarios />
    </main>

    <SecaoRepresentantes />
</template>

<script>
    import Destaque from '@/components/Destaque.vue';
    import Atividades from '@/components/Atividades.vue';
    import Horarios from '@/components/Horarios.vue';
    import SecaoRepresentantes from '@/components/SecaoRepresentantes.vue';

    export default {
        components: {
            Destaque,
            Atividades,
            Horarios,
            SecaoRepresentantes
        }
    }

</script>
