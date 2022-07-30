<template>
    <section id="horarios" class="horarios">
        <div class="divisor-triangular"></div>
        <h2>Horários de aula</h2>
        <img
            src="@/assets/imgs/HORARIO-OFICIAL-923A.jpg"
            alt="Horário das aulas da turma 923A"
            @dragstart="calculateInitialDistance"
        />
        <p v-if="teste">funcionou</p>
    </section>
</template>

<script>
    export default {
        data() {
            return {
                teste: false,
            }
        },
        methods: {
            calculateInitialDistance(ev) {
                this.teste = true;
            }
        }
    }
</script>
