0<script setup>
import { ref } from 'vue'

const ListaCompras = ref([
  {
    id: 1,
    nome: 'Martelo',
    preco: 49.9,
    adicionado: false,
    foto_url: "https://apiguana.vtexassets.com/arquivos/ids/155985/image1.jpg?v=637915902392770000"
  },
  {
    id: 2,
    nome: 'Cerrote',
    preco: 99.99,
    adicionado: false,
    foto_url: "https://cdn.pixabay.com/photo/2013/07/13/12/19/handsaw-159622_960_720.png"
  },
  {
    id: 3,
    nome: 'Chave de fenda',
    preco: 9.9,
    adicionado: false,
    foto_url: "https://www.hiperferro.com.br/media/catalog/product/cache/1/image/460x460/9df78eab33525d08d6e5fb8d27136e95/c/h/chave-de-fenda.png"

  },
  {
    id: 4,
    nome: 'Chave inglesa',
    preco: 199.9,
    adicionado: false,
    foto_url: "https://assets.stickpng.com/images/580b585b2edbce24c47b2be4.png"
  },  


  {
    id: 5,
    nome: 'Pregos',
    preco: 29.9,
    adicionado: false,
    foto_url: "https://macoe.com.br/wp-content/uploads/2017/04/Prego.png"
  },    


  {
    id: 6,
    nome: 'Óculos de proteção',
    preco: 99.9,
    adicionado: false,
    foto_url: "https://protectquality.com.br/wp-content/uploads/2021/08/RJ_Incolor__002_-removebg-preview.png"
  }
])

const Carrinho = ref([])

const carrinhoMostrar = ref(false)

function adicionarItemCarrinho(item) {
  if (item.adicionado == true) {
    alert('O item já está no carrinho!')
  } else {
    Carrinho.value.push({
      id: item.id,
      nome: item.nome,
      preco: item.preco,
      quantidade: 1
    })
  }

  ListaCompras.value[ListaCompras.value.indexOf(item)].adicionado = true;
  calcularTotal();
}

function incrementar(item) {
  Carrinho.value[Carrinho.value.indexOf(item)].quantidade += 1;
  calcularTotal();
}

function decrementar(item) {
  if (Carrinho.value[Carrinho.value.indexOf(item)].quantidade > 1) {
    Carrinho.value[Carrinho.value.indexOf(item)].quantidade -= 1
  }
  calcularTotal();
}

function removerItemCarrinho(item) {
  Carrinho.value.splice(Carrinho.value.indexOf(item), 1)
  console.log(Carrinho.value)
  ListaCompras.value[item.id - 1].adicionado = false
  calcularTotal();
}

const total = ref(0.00);

function calcularTotal() {
  total.value = 0.00;
  for (let item of Carrinho.value) {
    total.value += item.quantidade * item.preco;
  };
  total.value = total.value.toFixed(2)
}

</script>

<template>
  <h1>Materiais de construção</h1>
  <button @click="carrinhoMostrar = !carrinhoMostrar">Carrinho</button>
  <div class="itens">
      <div class="lista" v-for="item in ListaCompras" :key="item.id">
        <img :src="item.foto_url" alt="" height="200"> <br>
        {{ item.nome }}
        R$ {{ item.preco }}
        {{ item.id }}
        <button @click="adicionarItemCarrinho(item)">adicionar</button>
      </div>
    
  </div>
  <div class="carrinho" v-if="carrinhoMostrar">

    <h2>Carrinho</h2>
    <p>Total: R$ {{ total }}</p>
    <hr>
    <div>
      <li v-for="item of Carrinho" :key="item.id">
        {{ item.nome }}
        {{ item.preco }}
        ({{ item.quantidade }})
        <button @click="incrementar(item)">+</button>
        <button @click="decrementar(item)">-</button>
        <br />
        <button @click="removerItemCarrinho(item)">Remover</button>
      </li>
    </div>
  </div>
</template>

<style scoped>

.carrinho{
  margin-top: 20px;
  border: 1px solid;
}

.itens {
  display: flex;
}

.lista {
  margin: 10px;
}

</style>
0<script setup>
import { ref } from 'vue'

const ListaCompras = ref([
  {
    id: 1,
    nome: 'Martelo',
    preco: 49.9,
    adicionado: false,
    foto_url: "https://apiguana.vtexassets.com/arquivos/ids/155985/image1.jpg?v=637915902392770000"
  },
  {
    id: 2,
    nome: 'Cerrote',
    preco: 99.99,
    adicionado: false,
    foto_url: "https://cdn.pixabay.com/photo/2013/07/13/12/19/handsaw-159622_960_720.png"
  },
  {
    id: 3,
    nome: 'Chave de fenda',
    preco: 9.9,
    adicionado: false,
    foto_url: "https://www.hiperferro.com.br/media/catalog/product/cache/1/image/460x460/9df78eab33525d08d6e5fb8d27136e95/c/h/chave-de-fenda.png"

  },
  {
    id: 4,
    nome: 'Chave inglesa',
    preco: 199.9,
    adicionado: false,
    foto_url: "https://assets.stickpng.com/images/580b585b2edbce24c47b2be4.png"
  },  


  {
    id: 5,
    nome: 'Pregos',
    preco: 29.9,
    adicionado: false,
    foto_url: "https://macoe.com.br/wp-content/uploads/2017/04/Prego.png"
  },    


  {
    id: 6,
    nome: 'Óculos de proteção',
    preco: 99.9,
    adicionado: false,
    foto_url: "https://protectquality.com.br/wp-content/uploads/2021/08/RJ_Incolor__002_-removebg-preview.png"
  }
])

const Carrinho = ref([])

const carrinhoMostrar = ref(false)

function adicionarItemCarrinho(item) {
  if (item.adicionado == true) {
    alert('O item já está no carrinho!')
  } else {
    Carrinho.value.push({
      id: item.id,
      nome: item.nome,
      preco: item.preco,
      quantidade: 1
    })
  }

  ListaCompras.value[ListaCompras.value.indexOf(item)].adicionado = true;
  calcularTotal();
}

function incrementar(item) {
  Carrinho.value[Carrinho.value.indexOf(item)].quantidade += 1;
  calcularTotal();
}

function decrementar(item) {
  if (Carrinho.value[Carrinho.value.indexOf(item)].quantidade > 1) {
    Carrinho.value[Carrinho.value.indexOf(item)].quantidade -= 1
  }
  calcularTotal();
}

function removerItemCarrinho(item) {
  Carrinho.value.splice(Carrinho.value.indexOf(item), 1)
  console.log(Carrinho.value)
  ListaCompras.value[item.id - 1].adicionado = false
  calcularTotal();
}

const total = ref(0.00);

function calcularTotal() {
  total.value = 0.00;
  for (let item of Carrinho.value) {
    total.value += item.quantidade * item.preco;
  };
  total.value = total.value.toFixed(2)
}

</script>

<template>
  <h1>Materiais de construção</h1>
  <button @click="carrinhoMostrar = !carrinhoMostrar">Carrinho</button>
  <div class="itens">
      <div class="lista" v-for="item in ListaCompras" :key="item.id">
        <img :src="item.foto_url" alt="" height="200"> <br>
        {{ item.nome }}
        R$ {{ item.preco }}
        {{ item.id }}
        <button @click="adicionarItemCarrinho(item)">adicionar</button>
      </div>
    
  </div>
  <div class="carrinho" v-if="carrinhoMostrar">

    <h2>Carrinho</h2>
    <p>Total: R$ {{ total }}</p>
    <hr>
    <div>
      <li v-for="item of Carrinho" :key="item.id">
        {{ item.nome }}
        {{ item.preco }}
        ({{ item.quantidade }})
        <button @click="incrementar(item)">+</button>
        <button @click="decrementar(item)">-</button>
        <br />
        <button @click="removerItemCarrinho(item)">Remover</button>
      </li>
    </div>
  </div>
</template>

<style scoped>

.carrinho{
  margin-top: 20px;
  border: 1px solid;
}

.itens {
  display: flex;
}

.lista {
  margin: 10px;
}

</style>
<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <TheWelcome />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
