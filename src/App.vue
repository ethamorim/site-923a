<template>
    <header>
        <div class="menu" @click.left="alternarMenu()">
            <i class="material-icons-round" v-if="!menuAberto">menu</i>
            <i class="material-icons-round" v-else>menu_open</i>
        </div>

        <div class="logo">
            <img src="@/assets/imgs/logo-desenv-sistemas.png" alt="Brasão do curso de Desenvolvimento de Sistemas, criado por Bruno Lucas">
            <span class="turma">923A</span>
        </div>

        <Transition name="open">
            <nav v-if="menuAberto">
                <router-link to="/" @click="irParaSecao('home')">Home</router-link>
                <router-link to="/" @click="irParaSecao('avisos')">Avisos</router-link>
                <router-link to="/" @click="irParaSecao('horarios')">Horários</router-link>
                <router-link to="/" @click="irParaSecao('contatos')">Contatos</router-link>
                <router-link to="/">Atividades</router-link>
            </nav>
        </Transition>
    </header>

    <router-view />

    <footer>
        <div id="contatos" class="rodape">
            <section class="logo-ifal">
                <img src="@/assets/imgs/ifal-logo.png" alt="Logo do Instituto Federal de Alagoas">
                <p>
                    Instituto Federal de Educação, Ciência e Tecnologia de Alagoas
                    <br />
                    <strong>Campus Maceió</strong>
                </p>
            </section>

            <div class="outras-infos">
                <section class="outros-contatos">
                    <h3>Outros contatos</h3>

                    <ul>
                        <li>
                            <span class="email-turma">
                                <strong>email da turma:</strong>
                                <i
                                    class="material-icons-round"
                                    @click.left="abrirObsEmailTurma()">
                                    error_outline
                                </i>

                                <article
                                    id="obs-email-turma"
                                    :class="(obsEmailVisivel) ? 'obs-email-entrando' : ''"
                                    v-if="obsEmailVisivel"
                                    >
                                    <div class="triangulo-esquerda"></div>
                                    <p>Caso haja a necessidade de ter a senha, contatar os representantes da turma</p>
                                </article>
                            </span>
                            <span>devsistemas2020@gmail.com</span>
                        </li>
                        <li>
                            <span><strong>coordenação do curso:</strong></span>
                            <span>coord.info.maceio@ifal.edu.br</span>
                        </li>
                        <li>
                            <span><strong>coordenação de estágio (CREE):</strong></span>
                            <span>cree@ifal.edu.br</span>
                        </li>
                    </ul>

                    <p class="em-breve-professores">em breve os contatos dos professores estarão disponíveis</p>
                </section>

                <section class="outros-sites">
                    <h3>Outros sites</h3>

                    <ul>
                        <li>
                            <span><strong>sigaa:</strong></span>
                            <a href="https://sigaa.ifal.edu.br/sigaa/public/home.jsf" target="_blank">
                                <span class="site">sigaa.ifal.edu.br</span>
                                <i class="material-icons-round">open_in_new</i>
                            </a>
                        </li>
                        <li>
                            <span><strong>portal do ifal:</strong></span>
                            <a href="https://www2.ifal.edu.br/" target="_blank">
                                <span class="site">www2.ifal.edu.br</span>
                                <i class="material-icons-round">open_in_new</i>
                            </a>
                        </li>
                        <li>
                            <span><strong>mundo do trabalho:</strong></span>
                            <a href="mundodotrabalho.ifal.edu.br/" target="_blank">
                                <span class="site">mundodotrabalho.ifal.edu.br</span>
                                <i class="material-icons-round">open_in_new</i>
                            </a>
                        </li>
                    </ul>
                </section>
            </div>
        </div>

        <span class="creditos">2022 Desenvolvido por Ytalo Ethaniel Amorim</span>
    </footer>
</template>

<script>

    export default {
        data() {
            return {
                menuAberto: false,
                obsEmailVisivel: false,
            }
        },
        methods: {
            alternarMenu() {
                this.menuAberto = !this.menuAberto;
            },
            irParaSecao(secao) {
                document.getElementById(secao).scrollIntoView();
            },
            abrirObsEmailTurma() {
                this.obsEmailVisivel = true;

                const fechar = setInterval(() => {
                    if (this.obsEmailVisivel) {
                        this.obsEmailVisivel = false;
                        clearInterval(fechar);
                    }
                }, 2500);
            }
        }
    }

</script>
