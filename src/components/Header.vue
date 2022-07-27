<template>
    <header>
        <div class="menu" v-if="ehMobile" @click.left="alternarMenu()">
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
                <router-link to="/" @click="irParaSecao('atividades')">Atividades</router-link>
                <router-link to="/" @click="irParaSecao('horarios')">Horários</router-link>
                <router-link to="/" @click="irParaSecao('contatos')">Contatos</router-link>
            </nav>
        </Transition>
    </header>
</template>

<script>
    export default {
        data() {
            return {
                ehMobile: false,
                menuAberto: true,
            }
        },
        methods: {
            alternarMenu() {
                this.menuAberto = !this.menuAberto;
            },
            irParaSecao(secao) {
                document.getElementById(secao).scrollIntoView({behavior: 'smooth'});
            },
        },
        created() {
            if (
                navigator.userAgent.indexOf('Android') > -1 ||
                navigator.userAgent.indexOf('iPhone') > -1
            ) {
                this.ehMobile = true;
                this.menuAberto = false;
            }
        }
    }
</script>
