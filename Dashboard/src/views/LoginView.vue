<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()

// Dados do formulário
const email = ref('')
const senha = ref('')
const lembrar = ref(false)

// Controle da senha
const mostrarSenha = ref(false)

// Realiza o login
function fazerLogin() {
    if (!email.value || !senha.value) {
        alert('Preencha o e-mail e a senha.')
        return
    }

    // Usuário temporário enquanto não existe banco de dados
    const usuario = {
        email: email.value,
        senha: senha.value
    }

    localStorage.setItem(
        'usuarioLogado',
        JSON.stringify(usuario)
    )

    // Redireciona para a página principal
    router.push('/home')
}

// Mostra ou esconde a senha
function alternarSenha() {
    mostrarSenha.value = !mostrarSenha.value
}
</script>


<template>

    <main class="login-container">

        <!-- =========================
             PAINEL ESQUERDO
        ========================== -->

        <section class="painel-esquerdo">

            <!-- Logo -->

            <div class="logo">

                <div class="icone-logo">
                    💊
                </div>

                <div class="logo-texto">
                    <h2>
                        Med<span>Hora</span>
                    </h2>

                    <p>
                        Sua saúde em dia
                    </p>
                </div>

            </div>


            <!-- Frase -->

            <div class="frases">

                <div class="linha"></div>

                <h3>
                    “Pequenos cuidados hoje fazem uma grande diferença amanhã.”
                </h3>

            </div>


            <!-- Planta -->

            <div class="planta">
                🌿
            </div>

        </section>


        <!-- =========================
             PAINEL DIREITO
        ========================== -->

        <section class="painel-direita">

            <div class="form-box">

                <!-- Título -->

                <h1>
                    Entrar no sistema
                </h1>

                <p class="subtitulo">
                    Informe seus dados para acessar o MedHora.
                </p>


                <!-- =====================
                     E-MAIL
                ====================== -->

                <div class="input-group">

                    <label for="email">
                        E-mail
                    </label>

                    <div class="input-wrapper">

                        <span class="input-icon">
                            ✉
                        </span>

                        <input
                            v-model="email"
                            type="email"
                            id="email"
                            placeholder="Ex: seuemail@dominio.com"
                        >

                    </div>

                </div>


                <!-- =====================
                     SENHA
                ====================== -->

                <div class="input-group">

                    <label for="senha">
                        Senha
                    </label>

                    <div class="input-wrapper">

                        <span class="input-icon">
                            🔒
                        </span>

                        <input
                            v-model="senha"
                            :type="mostrarSenha ? 'text' : 'password'"
                            id="senha"
                            placeholder="Sua senha"
                        >

                        <button
                            type="button"
                            class="btn-mostrar-senha"
                            @click="alternarSenha"
                            aria-label="Mostrar ou esconder senha"
                        >
                            {{ mostrarSenha ? '◉' : '◌' }}
                        </button>

                    </div>

                </div>


                <!-- =====================
                     OPÇÕES
                ====================== -->

                <div class="opcoes">

                    <label
                        for="check"
                        class="lembrar"
                    >

                        <input
                            v-model="lembrar"
                            type="checkbox"
                            id="check"
                        >

                        <span>
                            Lembrar de mim
                        </span>

                    </label>


                    <a href="#">
                        Esqueceu sua senha?
                    </a>

                </div>


                <!-- =====================
                     BOTÃO LOGIN
                ====================== -->

                <button
                    type="button"
                    class="btn-login"
                    @click="fazerLogin"
                >
                    Entrar
                </button>


                <!-- =====================
                     SEPARADOR
                ====================== -->

                <div class="separador">

                    <span>
                        ou
                    </span>

                </div>


                <!-- =====================
                     CONTATO
                ====================== -->

                <div class="contact-box">

                    <h4>
                        Ainda não tem acesso?
                    </h4>

                    <p>
                        Entre em contato com o administrador do sistema.
                    </p>

                </div>

            </div>

        </section>

    </main>

</template>


<style scoped>

/* ==================================================
   RESET
================================================== */

:global(*) {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

:global(body) {
    font-family: Arial, Helvetica, sans-serif;
    background: #f4f8f8;
}


/* ==================================================
   CONTAINER PRINCIPAL
================================================== */

.login-container {
    width: 100%;
    min-height: 100vh;

    display: flex;
    justify-content: center;
    align-items: center;

    padding: 40px;

    background:
        radial-gradient(
            circle at 90% 10%,
            rgba(30, 185, 128, 0.08),
            transparent 25%
        ),
        #f4f8f8;
}


/* ==================================================
   PAINEL ESQUERDO
================================================== */

.painel-esquerdo {
    width: 50%;
    max-width: 550px;
    min-height: 660px;

    padding: 55px 60px;

    display: flex;
    flex-direction: column;

    background:
        radial-gradient(
            circle at 0% 100%,
            rgba(30, 185, 128, 0.12),
            transparent 45%
        ),
        #edf9f6;

    border-radius: 20px 0 0 20px;

    overflow: hidden;

    position: relative;
}


/* LOGO */

.logo {
    display: flex;
    align-items: center;
    gap: 18px;
}


/* FRASE */

.frases {
    max-width: 390px;

    margin-top: auto;
    margin-bottom: auto;

    position: relative;
    z-index: 2;
}

.linha {
    width: 55px;
    height: 5px;

    margin-bottom: 28px;

    background: #19b47d;

    border-radius: 10px;
}

.frases h3 {
    color: #116d65;

    font-size: 1.9rem;
    line-height: 1.45;

    font-weight: 400;
}


/* PLANTA */

.planta {
    position: absolute;

    left: 25px;
    bottom: 0;

    font-size: 6rem;

    opacity: 0.9;

    z-index: 1;
}

/* ==================================================
   PAINEL DIREITO
================================================== */

.painel-direita {
    width: 50%;
    max-width: 550px;
    min-height: 660px;

    padding: 55px 60px;

    display: flex;
    align-items: center;

    background: #ffffff;

    border-radius: 0 20px 20px 0;

    box-shadow: 0 15px 45px rgba(20, 50, 70, 0.08);
}


/* ==================================================
   FORMULÁRIO
================================================== */

.form-box {
    width: 100%;
}


/* Título */

.form-box h1 {
    margin-bottom: 8px;

    color: #102452;

    font-size: 2.5rem;
    line-height: 1.2;
}


/* Subtítulo */

.subtitulo {
    margin-bottom: 38px;

    color: #718096;

    font-size: 0.95rem;
}


/* ==================================================
   GRUPO DOS INPUTS
================================================== */

.input-group {
    width: 100%;

    margin-bottom: 22px;
}

.input-group label {
    display: block;

    margin-bottom: 8px;

    color: #17254b;

    font-size: 0.95rem;
    font-weight: 700;
}


/* ==================================================
   INPUT
================================================== */

.input-wrapper {
    width: 100%;
    height: 54px;

    display: flex;
    align-items: center;

    border: 1px solid #d8e0e8;

    border-radius: 9px;

    background: #ffffff;

    transition: border-color 0.2s, box-shadow 0.2s;
}

.input-wrapper:focus-within {
    border-color: #19b47d;

    box-shadow: 0 0 0 3px rgba(25, 180, 125, 0.1);
}


/* Ícone */

.input-icon {
    width: 45px;

    display: flex;
    justify-content: center;

    color: #718096;

    font-size: 18px;
}


/* Campo */

.input-wrapper input {
    flex: 1;

    height: 100%;

    padding: 0 8px;

    border: none;
    outline: none;

    color: #17254b;

    font-size: 0.95rem;
}

.input-wrapper input::placeholder {
    color: #a0aec0;
}


/* ==================================================
   BOTÃO MOSTRAR SENHA
================================================== */

.btn-mostrar-senha {
    width: 45px;
    height: 100%;

    border: none;

    background: transparent;

    color: #718096;

    cursor: pointer;

    font-size: 18px;
}


/* ==================================================
   OPÇÕES
================================================== */

.opcoes {
    display: flex;

    align-items: center;
    justify-content: space-between;

    margin: 4px 0 25px;

    font-size: 0.9rem;
}

.lembrar {
    display: flex;

    align-items: center;

    gap: 8px;

    color: #4a5568;

    cursor: pointer;
}

.lembrar input {
    width: 17px;
    height: 17px;

    accent-color: #19b47d;

    cursor: pointer;
}

.opcoes a {
    color: #14996b;

    font-weight: 700;

    text-decoration: none;
}

.opcoes a:hover {
    text-decoration: underline;
}


/* ==================================================
   BOTÃO LOGIN
================================================== */

.btn-login {
    width: 100%;
    height: 55px;

    border: none;
    border-radius: 9px;

    background: #12ae78;

    color: #ffffff;

    font-size: 1rem;
    font-weight: 700;

    cursor: pointer;

    transition: background 0.2s, transform 0.1s;
}

.btn-login:hover {
    background: #0e9969;
}

.btn-login:active {
    transform: scale(0.99);
}


/* ==================================================
   SEPARADOR
================================================== */

.separador {
    width: 100%;

    display: flex;

    align-items: center;

    gap: 15px;

    margin: 27px 0;
}

.separador::before,
.separador::after {
    content: "";

    height: 1px;

    flex: 1;

    background: #dce2e8;
}

.separador span {
    color: #667085;

    font-size: 0.9rem;
}


/* ==================================================
   CAIXA DE CONTATO
================================================== */

.contact-box {
    width: 100%;

    padding: 20px;

    text-align: center;

    border-radius: 9px;

    background: #f4f7fa;
}

.contact-box h4 {
    margin-bottom: 7px;

    color: #17254b;

    font-size: 0.95rem;
}

.contact-box p {
    color: #718096;

    font-size: 0.85rem;

    line-height: 1.4;
}


/* ==================================================
   RESPONSIVIDADE
================================================== */

@media (max-width: 950px) {

    .login-container {
        padding: 25px;
    }

    .painel-esquerdo,
    .painel-direita {
        padding: 45px;
    }

    .frases h3 {
        font-size: 1.6rem;
    }

    .form-box h1 {
        font-size: 2.2rem;
    }

}


@media (max-width: 750px) {

    .login-container {
        min-height: 100vh;

        padding: 20px;
    }

    .painel-esquerdo {
        display: none;
    }

    .painel-direita {
        width: 100%;
        max-width: 550px;
        min-height: auto;

        padding: 40px 30px;

        border-radius: 20px;
    }

}


@media (max-width: 450px) {

    .login-container {
        padding: 12px;
    }

    .painel-direita {
        padding: 30px 20px;
    }

    .form-box h1 {
        font-size: 1.9rem;
    }

    .opcoes {
        align-items: flex-start;

        gap: 15px;
    }

    .opcoes a {
        text-align: right;
    }

}

</style>