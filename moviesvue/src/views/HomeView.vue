<template>
  <div class="home">
    <section class="hero is-medium is-dark mb-6">
        <div class="hero-body has-text-centered" id="navbarsneaker">
            <p class="title mb-6">
                Bienvenido a Sneaker Hunters
            </p>
            <p class="subtitle">
                Todos los sneakers que buscas
            </p>
        </div>
        <div id="carouselExampleIndicators" class="carousel slide" data-bs-ride="true">
    <div class="carousel-indicators">
      <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="0" class="active" aria-current="true" aria-label="Slide 1"></button>
      <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="1" aria-label="Slide 2"></button>
      <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="2" aria-label="Slide 3"></button>
      <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="3" aria-label="Slide 0"></button>
    </div>
    <div class="carousel-inner">
      <div class="carousel-item active">
        <router-link to="nike/Dunk-LowSP/">
        <img src="../views/images/NikeDunkLow.png" class="d-block w-100" alt="...">
        </router-link>
      </div>
      <div class="carousel-item">
        <router-link to="adidas/Yeezy-700-V3/">
        <img src="../views/images/Yeezy700.png" class="d-block w-100" alt="...">
        </router-link>
      </div>
      <div class="carousel-item">
        <router-link to="nike/Dunk-PandaLow/">
        <img src="../views/images/NikeDunkPanda.png" class="d-block w-80" alt="...">
        </router-link>
      </div>
      <div class="carousel-item">
        <router-link to="adidas/Yeezy-RNR-Black/">
        <img src="../views/images/YeezyFoam.png" class="d-block w-80" alt="...">
        </router-link>
      </div>
    </div>
    <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide="prev">
      <span class="carousel-control-prev-icon" aria-hidden="true"></span>
      <span class="visually-hidden">Previous</span>
    </button>
    <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide="next">
      <span class="carousel-control-next-icon" aria-hidden="true"></span>
      <span class="visually-hidden">Next</span>
    </button>
  </div>
    </section>
    <div class="columns is-multiline" id="AcercaDeNosotros">
      <div class="column is-12">
          <h2 class="is-size-2 has-text-centered">Acerca de nosotros</h2>
          <p id="info" class="hero-body has-text-centered">Somos una empresa en línea establecida desde hace más de 5 años dedicada a la comercialización de los sneakers más reconocidos, contamos con los últimos lanzamientos a nivel mundial</p>
      </div>
      <div id="about-2">
        <div class="content-box-lg">
          <div class="container">
            <div class="row" >
              <div class="col-md-4">
                <div class="about-item text-center">
                  <i class="fa fa-book"></i>
                  <h3>Misión</h3>
                  <hr>
                  <p>Nuestra misión es ofrecer una experiencia de calidad total a todos los clientes que forman parte de la comunidad, avalamos nuestros servicios dándote la oportunidad de adquirir tus pares favoritos y llevándolos hasta la puerta de tu hogar.</p>
                </div>
              </div>
              <div class="col-md-4">
                <div class="about-item text-center">
                  <i class="fa fa-globe"></i>
                  <h3>Visión</h3>
                  <hr>
                  <p>Nuestra visión para los proximos es cada vez mas incrementar la cantidad de pares que conseguimos para poder llegar ser un distribuidor de las propias marcas</p>
                </div>
              </div>
              <div class="col-md-4">
                <div class="about-item text-center">
                  <i class="fa fa-star "></i>
                  <h3>Logros</h3>
                  <hr>
                  <p>Dentro de los 5 años que llevamos en el mercado hemos conseguido alrededor de mas de 1000 pares vendidos, logrando tener nuestra pagina funcional.</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="columns is-multiline">
      <div class="column is-12">
          <h2 class="is-size-2 has-text-centered">Ultimos productos</h2>
      </div>
      <ProductBox 
        v-for="product in latestProducts"
        v-bind:key="product.id"
        v-bind:product="product" />
      

    </div>

    <div class="columns is-multiline" id="PreguntasFrecuentes">
      <div class="column is-12">
          <h2 class="is-size-2 has-text-centered">Preguntas frecuentes</h2>
          <ul>
            <li><b>¿Dónde puedo solicitar una devolución? </b></li>
            <p>A través de nuestro Servicio al Cliente por correo en SneakerHunters@gmail.com </p>
            <li><b>¿Cuánto tiempo tengo para solicitar una devolución?  </b></li>
            <p>Si es por error de proceso, pedido incompleto o defecto de fábrica, tienes que reportarlo a nuestro Servicio al Cliente en un lapso no mayor a 48 horas a partir de recibido tu paquete. </p>
            <p>Si es por insatisfacción de producto, a partir de 24 hrs después de haber recibido tu pedido y dentro de un plazo no mayor a 30 días naturales después de la fecha de tu orden de compra</p>
            <li><b>¿Qué productos no aplican para Cambios o Devoluciones?</b></li>
            <p>Los productos de lanzamiento, ediciones especiales, productos en promoción o con descuento.</p>
            <li><b>¿Dónde puedo solicitar una devolución?</b> </li>
            <p>A través de nuestro Servicio al Cliente por correo en SneakerHunters@gmail.com </p>
          </ul>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

import ProductBox from '@/components/ProductBox'

export default {
  name: 'HomeView',
  data(){
    return{
      latestProducts: []
    }
  },
  components: {
    ProductBox
  },
  mounted() {
    this.getLatestProducts()

    document.title = ' SneakerHunters '
  },
  methods: {
    async getLatestProducts() {
      this.$store.commit('setIsLoading', true)

      await axios
        .get('/api/v1/latest-products/')
        .then(response => {
          this.latestProducts = response.data
        })
        .catch(error => {
          console.log(error)
        })

      this.$store.commit('setIsLoading', false)
    }
  }
}
</script>
<style>
#navbarsneaker{
  background-color: #000;
}
#info{
  font-size: 20px;
}
</style>