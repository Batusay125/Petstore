<template>
  <header>
    <div class="navbar navbar-default">
      <div class="navbar-header">
        <h1>
          <router-link :to="{ name: 'iMain'}"> <!--Ten element tworzy powiązanie z trasą Main (DZIAŁA BEZ)-->
            {{ sitename }}
          </router-link>
        </h1>
      </div>
      <div class="nav navbar-nav navbar-right cart">
          <router-link active-class="active route-link-exact-active" tag="button" class="btn btn-default btn-lg" :to='{name: "Form"}'>
          <span class="glyphicon glyphicon-shopping-cart">{{cartItemCount}}</span>Kasa
          </router-link>
      </div>
    </div>
  </header>
</template>
<!------------------------------------------------------------------------------------------------------------------------------------------------------->
<script>
export default {
  name: "my-header",
  data() {
    return {
      sitename: "Skład dla zwierzaków :: Vue.js",
    };
  },
  props: ["cartItemCount"],
  methods: {
    showCheckout() {
      this.$router.push({ name: "Form" }); // powoduje użycie w aplikacji trasy Form (DZIAŁA BEZ)
    },
  },
};
</script>
<!------------------------------------------------------------------------------------------------------------------------------------------------------->

<!-- Dodaj atrybut "scoped", by ograniczyć zasięg stylów CSS 
     do tylko tego komponentu. -->
<style scoped>
a {
  text-decoration: none;
  color: black;
}
.route-link-exact-active {
    color: router;
}
</style>