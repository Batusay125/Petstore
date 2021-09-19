<template>
  <div>
    <my-header></my-header> <!--KOMPONENT MY-HEADER-->
    <h1>Identyfikator: {{ $route.params.id }}</h1>
    <div class="row">
      <div class="col-md-5 col-md-offset-0">
        <figure>
          <img class="product" v-bind:src="product.image" />
        </figure>
      </div>
      <div class="col-md-6 col-md-offset-0 description">
        <h1>{{ product.title }}</h1>
        <p v-html="product.description"></p>
        <p class="price">
          {{ product.price }}
        </p>
        <button @click="edit">Edytuj produkt</button>
        <router-view></router-view> <!--KOMPONENT $router-view, STANOWIĄCY PUNKT WEJŚCIA TRASY-->
      </div>
    </div>
  </div>
</template>
<!------------------------------------------------------------------------------------------------------------------------------------------------------->

  <script>
import MyHeader from "./Header.vue";
export default {
  components: { MyHeader },
  data() {
    return {
      product: "",
    };
  },
  created: function () {
    axios.get("/static/products.json").then((response) => { //POBRANIE STATYCZNEGO PLIKU PRZY UŻYCIU AXIOS
      this.product = response.data.products.filter( //PRZEFILTROWANIE POBIERANYCH DANYCH
        (data) => data.id == this.$route.params.id
      )[0]; // W THIS.PRODUT ZOSTANĄ ZAPISANE JEDYNIE DANE PASUJĄCE DO PARAMETRU TRASY
      this.product.image = "/" + this.product.image; // DODANIE'/' NA POCZĄTKU PRODUCT.IMAGE W CELU UZYSKANIA PRAWIDŁOWEJ ŚCIEŻKI WZGLĘDNEJ
    });
  },
  methods: {
    edit() {
      this.$router.push({ name: "Edit" }); //METODA $router.push AKTYWUJE TRASĘ EDIT
    },
  },
};
</script>
<!------------------------------------------------------------------------------------------------------------------------------------------------------->
