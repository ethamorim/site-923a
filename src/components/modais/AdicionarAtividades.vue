<template>
    <div class="modal-overlay">
        <form action="#" class="modal-conteiner modal" @click="mudarMensagemErro('')">
            <div class="modal__header">
                <legend>Adicione uma atividade</legend>
                <i class="material-icons-round" @click.left="$emit('fecharModal')">
                    close
                </i>
            </div>

            <fieldset class="materias" :class="corMateria">
                <div class="posicao-input">
                    <label
                        for="materia"
                        :class="(corMateria === 'branco') ? 'textoPreto' : ''">
                        Matéria:
                    </label>
                    <select id="materia" name="materia" v-model="atividade.materia">
                        <option value="">Selecione a matéria</option>
                        <option
                            v-for="(materia, i) in materias"
                            :key="i"
                            :value="materia[0]">
                            {{ materia[1] }}
                        </option>
                    </select>
                </div>

                <div class="posicao-input cor">
                    <label
                        :class="(corMateria === 'branco') ? 'textoPreto' : ''">
                        Cor:
                    </label>
                    <div
                        class="picker cor-escolhida"
                        :class="corMateria"
                        @click="toggleColorPicker">
                    </div>

                    <ColorPicker
                        v-if="colorPickerAberto"
                        :corEscolhida="corMateria"
                        @escolherCor="escolherCor"
                        @fechar="fecharColorPicker"
                    />
                </div>
            </fieldset>

            <fieldset class="info-atividade posicao-input">
                <label for="titulo">Titulo da atividade:</label>
                <input type="text" id="titulo" v-model="atividade.titulo">
            </fieldset>

            <fieldset class="data-atividade posicao-input">
                <label for="data-entrega">Data de entrega</label>

                <div class="data-atividade__conteiner">
                    <div class="data">
                        <input type="date" id="data-entrega" v-model="data">
                    </div>

                    <div class="horas">
                        <select name="horas" v-model="horaEntrega">
                            <option
                                v-for="hora in horas"
                                :key="hora"
                                :value="hora">
                                {{ hora }}
                            </option>
                        </select>

                        <span>:</span>

                        <select name="minutos" v-model="minutoEntrega">
                            <option
                                v-for="minuto in minutos"
                                :key="minuto"
                                :value="minuto">
                                {{ minuto }}
                            </option>
                        </select>
                    </div>
                </div>
            </fieldset>

            <fieldset class="posicao-input descricao">
                <label for="descricao">Descrição:</label>
                <textarea
                    name="descricao"
                    id="descricao"
                    placeholder="Digite os detalhes da atividade aqui"
                    v-model="atividade.descricao">
                </textarea>
            </fieldset>

            <fieldset class="posicao-input link-class">
                <label for="link-classroom">Link do Classroom:</label>
                <input
                    type="text"
                    id="link-classroom"
                    placeholder="https://classroom.google.com"
                    v-model="linkClassroom">
            </fieldset>

            <fieldset class="adicionar-ativ">
                <span v-show="mensagemErro.length" class="mensagem-erro">{{ mensagemErro }}</span>
                <button @click.prevent="adicionarAtividade">Adicionar</button>
            </fieldset>
        </form>
    </div>
</template>

<script>
    import ColorPicker from './ColorPicker.vue';
    const axios = require('axios').default;

    export default {
        components: {
            ColorPicker
        },
        computed: {
            horas() {
                return this.retornarArrayDeNumeros(23);
            },
            minutos() {
                return this.retornarArrayDeNumeros(59);
            },
            corMateria() {
                return this.atividade.cor;
            },
            dataEntrega() {
                const dataSeparada = this.data.split('-');
                const dataReversa = dataSeparada.reverse();
                const dataFormatada = dataReversa.join('-');

                const horaEntrega = this.horaEntrega + ":" + this.minutoEntrega;

                return dataFormatada + " " + horaEntrega;
            }
        },
        data() {
            return {
                materias: [
                    ["APSI", "Análise e Projeto de Software e Interface Humano-Máquina"],
                    ["LSOR", "Laboratórios de Sistemas Operacionais e Redes"],
                    ["HIST", "História"],
                    ["TEPI", "Tópicos Especiais e Projeto Integrador"],
                    ["FISC", "Física"],
                    ["LPOR", "Língua Portuguesa"],
                    ["MATE", "Matemática"],
                    ["LESP", "Língua Espanhola"],
                    ["QUIM", "Química"],
                    ["BIOL", "Biologia"],
                    ["FILO", "Filosofia"],
                    ["GOST", "Gestão Organizacional e Segurança do Trabalho"],
                    ["SOCI", "Sociologia"],
                    ["PNDI", "Projeto de Negócios Digitais"],
                    ["GEOG", "Geografia"],
                ],
                colorPickerAberto: false,
                data: '',
                horaEntrega: '00',
                minutoEntrega: '00',
                linkClassroom: '',
                atividade: {
                    materia: '',
                    cor: 'preto',
                    titulo: '',
                    descricao: '',
                },
                mensagemErro: '',
            }
        },
        methods: {
            toggleColorPicker() {
                this.colorPickerAberto = !this.colorPickerAberto;
            },
            fecharColorPicker() {
                this.colorPickerAberto = false;
            },
            escolherCor(cor) {
                this.atividade.cor = cor;
            },
            retornarArrayDeNumeros(num) {
                const numeros = [];
                for (let i = 0; i <= num; i++) {
                    let strNum = i.toString();

                    if (strNum.length === 1) {
                        strNum = '0' + strNum;
                    }
                    numeros.push(strNum);
                }
                return numeros;
            },
            adicionarAtividade() {
                if (this.linkClassroom.length) {
                    this.atividade['linkClassroom'] = this.linkClassroom;
                }
                this.atividade['dataEntrega'] = this.dataEntrega;

                axios.post('https://ws-site-923a.herokuapp.com/atividades', this.atividade)
                    .then((promise) => {
                        this.$emit('fecharModal');
                        this.$emit('reload');
                    })
                    .catch((rejected) => {
                        const response = JSON.parse(rejected.request.response);
                        this.mudarMensagemErro(response.mensagem);
                    });
            },
            mudarMensagemErro(mensagem) {
                this.mensagemErro = mensagem;
            }
        },
        mounted() {
            document.body.style.overflowY = 'hidden';
        },
        beforeUnmount() {
            document.body.style.overflowY = 'auto';
        }
    }
</script>
