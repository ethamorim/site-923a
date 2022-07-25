<template>
    <section class="card-representante">
        <div class="rep">
            <div class="bandeira" :class="rep.bandeira">
                <img :src="foto" :alt="rep.altImagem">
            </div>

            <div class="rep__info">
                <div class="conhecendo">
                    <h3>{{ rep.nome }} <strong>"{{ rep.apelido }}"</strong> {{ rep.sobrenome }}</h3>
                    <span class="titulo">{{ rep.titulo }}</span>
                </div>

                <div class="sobre">
                    <p>
                        {{ rep.sobre }}
                    </p>
                </div>
            </div>
        </div>

        <div class="contato">
            <h4>contato</h4>
            <ul>
                <li>
                    <strong>telefone:</strong> {{ rep.telefone }}
                </li>

                <li>
                    <strong>email:</strong> {{ rep.email }}
                </li>
            </ul>
        </div>
    </section>
</template>

<script>

    export default {
        props: ['rep'],
        data() {
            return {
                foto: null
            }
        },
        mounted() {
            this.foto = '/' + this.rep.imagem;
        }
    }

</script>
