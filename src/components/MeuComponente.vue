<template>
  <div>
    <h2>Cadastro de Filmes</h2>
    
    <div>
      <label for="nome">Nome do Filme:</label>
      <input id="nome" v-model="novoFilme.nome" type="text" placeholder="Nome do filme" />
    </div>
    
    <div>
      <label for="genero">Gênero:</label>
      <input id="genero" v-model="novoFilme.genero" type="text" placeholder="Gênero" />
    </div>
    
    <div>
      <label for="ano">Ano de Lançamento:</label>
      <input id="ano" v-model="novoFilme.ano" type="number" placeholder="Ano de lançamento" />
    </div>
    
    <button @click="adicionarFilme">Adicionar Filme</button>
    
    <ul>
      <li v-for="(filme, index) in filmes" :key="index">
        <p><strong>Nome:</strong> {{ filme.nome }}</p>
        <p><strong>Gênero:</strong> {{ filme.genero }}</p>
        <p><strong>Ano de Lançamento:</strong> {{ filme.ano }}</p>
        <button @click="removerFilme(index)">Deletar</button>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref } from 'vue'

// Definindo as características do filme
const novoFilme = ref({
  nome: '',
  genero: '',
  ano: ''
})

// Lista de filmes
const filmes = ref([])

// Função para adicionar um novo filme à lista
function adicionarFilme() {
  if (novoFilme.value.nome && novoFilme.value.genero && novoFilme.value.ano) {
    filmes.value.push({ ...novoFilme.value })
    // Limpar os campos após adicionar
    novoFilme.value = { nome: '', genero: '', ano: '' }
  }
}

// Função para remover um filme da lista
function removerFilme(index) {
  filmes.value.splice(index, 1)
}
</script>

<style scoped>
h2 {
  font-size: 24px;
  margin-bottom: 10px;
}

input {
  margin: 5px 0;
  padding: 8px;
  width: 200px;
  display: block;
}

button {
  margin-top: 10px;
  padding: 10px;
  background-color: #007BFF;
  color: white;
  border: none;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin: 10px 0;
  font-size: 18px;
}

li button {
  margin-top: 10px;
  background-color: red;
}

p {
  margin: 5px 0;
}
</style>
