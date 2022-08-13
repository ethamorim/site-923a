<template>
    <div class="color-picker">
        <div class="picker holder"></div>
        <div class="picker"
            v-for="(color, i) in colors"
            :key="i"
            :class="(corEscolhida === color) ? 'preto' : color"
            @click="escolherCor(color)">
        </div>
    </div>
</template>

<script>
    export default {
        props: ['corEscolhida'],
        data() {
            return {
                colors: [
                    'vermelho',
                    'laranja',
                    'amarelo',
                    'verde',
                    'azul-claro',
                    'azul',
                    'roxo',
                    'rosa',
                    'branco'
                ],
            }
        },
        methods: {
            escolherCor(cor) {
                if (cor === this.corEscolhida) {
                    this.$emit('escolherCor', 'preto');
                } else {
                    this.$emit('escolherCor', cor);
                }
                this.$emit('fechar');
            },
        },
    }
</script>
