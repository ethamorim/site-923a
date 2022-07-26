<template>
    <div class="fardas" :class="farda.nome">
        <img
        class="frente"
        :src="farda.frente"
        :alt="`Frente da farda ${farda.nome} do curso de Desenvolvimento de Sistemas`" />

        <img
        class="verso"
        :src="farda.verso"
        :alt="`Verso da farda ${farda.nome} do curso de Desenvolvimento de Sistemas`" />
    </div>
</template>

<script>

    export default {
        props: ['farda'],
    }

</script>
