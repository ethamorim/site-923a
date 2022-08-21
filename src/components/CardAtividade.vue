<template>
    <div class="card-atividade">
        <div
            class="card-atividade__materia"
            :class="atividade.cor">
            <span>
                {{ atividade.materia }}
            </span>
        </div>

        <div class="card-atividade__info">
            <div class="descricao">
                <div class="descricao__header">
                    <h3>{{ atividade.titulo }}</h3>
                    <i class="material-icons-round" @click.left="removerAtividade">delete</i>
                </div>
                <p>{{ atividade.descricao }}</p>
            </div>

            <div class="detalhes">
                <span><strong>até:</strong> {{ dataEntrega }}</span>

                <a v-if="atividade.linkClassroom" :href="atividade.linkClassroom" target="_blank">
                    <i class="material-icons-round">assignment_ind</i>
                </a>
            </div>
        </div>
    </div>
</template>

<script>
    const axios = require('axios').default;

    export default {
        props: ['atividade'],
        computed: {
            dataEntrega() {
                const data = new Date(this.atividade.dataEntrega);
                const dataLocal = data.toLocaleDateString('pt-br', {dateStyle: 'medium'});
                const horaLocal = data.toLocaleTimeString('pt-br', {timeStyle: 'short'});

                return dataLocal + ' ' + horaLocal;
            }
        },
        methods: {
            removerAtividade() {
                axios.delete('https://ws-site-923a.herokuapp.com/removerAtividade', {
                    data: {
                        "id": this.atividade.id
                        }
                    }
                ).then(promise => {
                    this.$emit('getAtividades')
                });
            }
        }
    }
</script>
