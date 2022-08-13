<template>
    <div class="modal-overlay" @click.left="$emit('fecharModal')">
        <form action="#" class="modal-conteiner modal" @click.stop>
            <div class="modal__header">
                <legend>Adicione uma atividade</legend>
                <i class="material-icons-round" @click.left="$emit('fecharModal')">
                    close
                </i>
            </div>

            <fieldset class="materias" :class="corMateria">
                <div class="posicao-input">
                    <label for="materia"
                        :class="(corMateria === 'branco') ? 'textoPreto' : ''">
                        Matéria:
                    </label>
                    <select id="materia" name="materia">
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

            <fieldset class="info-atividade">
                <div class="posicao-input">
                    <label for="">Titulo da atividade:</label>
                    <input type="text">
                </div>

                <div class="posicao-input">
                    <label for="">Data de entrega</label>
                    <input type="date">
                </div>
            </fieldset>

            <fieldset class="posicao-input descricao">
                <label for="">Descrição:</label>
                <textarea name="" id="" placeholder="Digite os detalhes da atividade aqui"></textarea>
            </fieldset>

            <fieldset class="posicao-input link-class">
                <label for="">Link do Classroom</label>
                <input type="text" placeholder="https://classroom.google.com">
            </fieldset>

            <fieldset class="adicionar-ativ">
                <button @click.prevent>Adicionar</button>
            </fieldset>
        </form>
    </div>
</template>

<script>
    import ColorPicker from './ColorPicker.vue';

    export default {
        components: {
            ColorPicker
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
                corMateria: 'preto',
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
                this.corMateria = cor;
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
