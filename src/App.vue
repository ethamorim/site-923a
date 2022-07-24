<template>
    <header>
        <div class="logo">
            <img src="@/assets/imgs/logo-desenv-sistemas.png" alt="Brasão do curso de Desenvolvimento de Sistemas, criado por Bruno Lucas">
            <span class="turma">923A</span>
        </div>

        <nav>
            <a href="#">Home</a>
            <a href="#">Avisos</a>
            <a href="#">Horários</a>
            <a href="#">Contatos</a>
            <router-link to="/">Atividades</router-link>
        </nav>
    </header>

    <router-view />

    <footer>

    </footer>
</template>
