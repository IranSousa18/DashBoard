<template>
<div class="login-container">

    <!-- Lado Esquerdo -->
    <div class="painel-esquerdo">
        <div class="logo">
            💊
            <div>
                <h2>Hora do Remédio</h2>
                <p>Sua saúde em dia</p>
            </div>
        </div>


        <div class="frases">
            <div class="linha"></div>
            <h3>"Pequenos cuidados hoje fazem uma grande diferença amanhã."</h3>
        </div>

        <div class="planta">
            🌿
        </div>
    </div>

    <!-- Lado Direito-->
    <div class="painel-direita">
        <div class="form-box">
            <h1>Entra no sistema</h1>
            <p class="subtitulo"> Informe seus dados para entrar no MedHora</p>

            <!-- Inserir E-mail-->
            <div class="input-group">
                <label for="email">E-mail: </label>
                <input  type="email" id="email" placeholder="Ex: seuemail@gmail.com"/>
            </div>


            <!-- Inserir Senha -->
            <div class="input-group">
                <label for="senha">Senha: </label>
                <input type="password" id="senha" placeholder="Sua senha"/>
            </div>

            <div class="opcoes">
                <label for="check">
                    <input type="checkbox" name="check" id="check">Lembrar de mim
                </label>

                <a href="#">Esqueceu sua senha?</a>
            </div>

            <button class="btn-login">Entrar</button>

            <div class="separador">
                <span>ou</span>
            </div>

            <div class="contact-box">
                <h4>Ainda não tem acesso?</h4>
                <p>Entre em contato com o administrador do sistema</p>
            </div>

        </div>
    </div>

</div>

</template>


<script setup>
import { ref } from 'vue';
const email = ref("")
</script>




<style scoped>



</style>