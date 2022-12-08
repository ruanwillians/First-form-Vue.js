<template>
  <div id="app">
    <div class="conteudo">
      <form class="painel" v-if="invited === false">
        <div class="cabecalho">Formulário</div>
        <Rotulo name="Nome"></Rotulo>
        <input type="text" placeholder="Digite seu nome" v-model="user.name" />

        <Rotulo name="Sobrenome"></Rotulo>
        <input
          type="text"
          placeholder="Digite seu sobrenomenome"
          v-model="user.lastname"
        />

        <Rotulo name="Email"></Rotulo>
        <input
          type="email"
          placeholder="Digite seu email"
          v-model="user.email"
        />

        <Rotulo name="Password"></Rotulo>
        <input
          type="email"
          placeholder="Digite sua senha"
          v-model="user.password"
        />

        <div class="therms">
          <input type="checkbox" v-model="user.therms" />
          <p>
            Concorda com os <a href="https://www.google.com">termos</a> do
            contrato?
          </p>
        </div>

        <button @click.prevent="enviteForm" v-if="user.therms === true">Enviar</button>

        <!-- Exercicio 03 -->
        <!-- Crie um componente personalizado NomeCompleto -->
        <!-- Esse componente deve receber Nome e Sobrenome -->
      </form>

      <div class="painel" v-if="invited === true">
        <div class="cabecalho">Resultado</div>
        <div class="container">
          <h2>Nome:</h2>
          <p>{{ user.name }}</p>
        </div>

        <div class="container">
          <h2>Sobrenome:</h2>
          <p>{{ user.lastname }}</p>
        </div>

        <complete-name :name="user.name" :lastname="user.lastname" />

        <div class="container">
          <h2>Email</h2>
          <p>{{ user.email }}</p>
        </div>

        <div class="container">
          <h2>Senha</h2>
          <p>{{ user.password }}</p>
        </div>

        <div class="container">
          <h2>Termos</h2>
          <p>{{ user.therms }}</p>
        </div>

        <button @click="invited = false">Voltar</button>
      </div>
    </div>
  </div>
</template>

<script>
import Rotulo from "./components/Rotulo.vue";
import CompleteName from "./components/CompleteName.vue";

export default {
  name: "app",
  components: { Rotulo, CompleteName },
  data() {
    return {
      invited: false,
      user: {
        name: "",
        lastname: "",
        email: "",
        password: "",
        therms: true,
      },
    };
  },
  methods: {
    enviteForm() {
      this.invited = true;
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
body {
  background-color: #ececec;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
  align-items: center;
  justify-content: center;
}

.painel {
  background: #fff;
  padding: 20px;
  border: 1px solid #aaa;
  border-radius: 5px;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  min-width: 20vw;
  max-height: 80vh;
  margin-top: 3em;
}

.painel .cabecalho {
  background-color: #ddd;
  padding: 10px 0px;
  border-radius: 5px;
  font-size: 1.4rem;
  min-width: 100%;
}

 button  {
  float: right;
  margin: 10px 0px;
  padding: 10px 20px;
  font-size: 1.4rem;
  border-radius: 5px;
  color: #fff;
  background-color: #0000F5;
  cursor: pointer;
  border: none;
}

#app form button:hover {
  opacity: 0.8;
}

#app h1 {
  font-weight: 200;
  margin: 20px;
  padding: 0;
}

.mr-4 {
  margin-right: 40px;
}

.container {
  min-height: 3em;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  margin-top: .5em;
}

input,
textarea,
select {
  flex: 1;
  font-size: 1.4rem;
  outline: none;
  border: 1px solid #ddd;
  border-radius: 5px;
  padding: 5px;
}

input:focus {
  border: 1px solid #bbb;
}

.therms {
  display: flex;
  flex-direction: row;
  margin-top: 1em;
  margin-bottom: .5em;
}

.therms a {
  color: #0000F5;
  text-decoration: none;
  cursor: pointer;
}
</style>
