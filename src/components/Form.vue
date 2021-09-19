<template>
  <div>
    <my-header :cartItemCount="cartItemCount"></my-header>
    <div class="row">
      <div class="col-md-10 col-md-offset-1">
        <div class="panel panel-info">
          <div class="panel-heading">Formularz zamówienia</div>
          <div class="panel-body">
            <div class="form-group">
              <div class="col-md-12">
                <h4><strong>Podaj informacje o sobie</strong></h4>
              </div>
            </div>
            <div class="form-group">
              <div class="col-md-6">
                <strong>Imię:</strong>
                <input v-model.trim="order.firstName" class="form-control" />
              </div>
              <div class="col-md-6">
                <strong>Nazwisko:</strong>
                <input v-model.trim="order.lastName" class="form-control" />
              </div>
            </div>
            <div class="form-group">
              <div class="col-md-12"><strong>Adres:</strong></div>
              <div class="col-md-12">
                <input v-model.trim="order.address" class="form-control" />
              </div>
            </div>
            <div class="form-group">
              <div class="col-md-12"><strong>Miejscowość:</strong></div>
              <div class="col-md-12">
                <input v-model.trim="order.city" class="form-control" />
              </div>
            </div>
            <div class="form-group">
              <div class="col-md-3">
                <strong>Województwo:</strong>
                <select v-model="order.state" class="form-control">
                  <option disabled value="">Województwo</option>
                  <option v-for="state in states">
                    {{ state }}
                  </option>
                </select>
              </div>
            </div>
            <div class="form-group">
              <div class="col-md-5 col-md-offset-4">
                <strong>Kod pocztowy:</strong>
                <input
                  v-model.number="order.zip"
                  class="form-control"
                  type="number"
                />
              </div>
            </div>
            <div class="form-group">
              <div class="col-md-6 boxes">
                <input
                  type="checkbox"
                  id="gift"
                  value="true"
                  v-bind:true-value="order.sendGift"
                  v-bind:false-value="order.dontSendGift"
                  v-model="order.gift"
                />
                <label for="gift">Wysłać jako prezent?</label>
              </div>
            </div>
            <!-- koniec form-group -->
            <div class="form-group">
              <div class="col-md-6 boxes">
                <input
                  type="radio"
                  id="home"
                  v-bind:value="order.home"
                  v-model="order.method"
                />
                <label for="home">Domowy</label>
                <input
                  type="radio"
                  id="business"
                  v-bind:value="order.business"
                  v-model="order.method"
                />
                <label for="business">Firmowy</label>
              </div>
            </div>
            <!-- koniec form-group-->
            <div class="form-group">
              <div class="col-md-6">
                <button
                  type="submit"
                  class="btn btn-primary submit"
                  v-on:click="submitForm"
                >
                  Złóż zamówienie
                </button>
              </div>
              <!-- koniec col-md-6-->
            </div>
            <!-- koniec form-group-->
            <div class="col-md-12 verify">
              <pre>
                         Imię: {{ order.firstName }}
                     Nazwisko: {{ order.lastName }}
                        Adres: {{ order.address }}
                  Miejscowość: {{ order.city }}
                 Kod pocztowy: {{ order.zip }}
                  Województwo: {{ order.state }}
                       Metoda: {{ order.method }}
                      Prezent: {{ order.gift }}
              </pre>
            </div>
            <!-- koniec col-md-12 verify-->
          </div>
          <!-- koniec panel-body-->
        </div>
        <!-- koniec panel panel-info-->
      </div>
      <!-- koniec col-md-10 col-md-offset-1-->
    </div>
    <!-- koniec row-->
  </div>
</template>
<!------------------------------------------------------------------------------------------------------------------------------------------------------->

<script>
import MyHeader from "./Header.vue";
export default {
  name: "Form",
  props: ["cartItemCount"],
  data() {
    return {
      states: {
        DL: "Dolnośląskie",
        KP: "Kujawsko-pomorskie",
        LB: "Lubelskie",
        LU: "Lubuskie",
      },
      order: {
        firstName: "",
        lastName: "",
        address: "",
        city: "",
        zip: "",
        state: "",
        method: "Adres domowy",
        business: "Adres firmowy",
        home: "Adres domowy",
        gift: "Wyślij jako prezent",
        sendGift: "Wyślij jako prezent",
        dontSendGift: "Nie wysyłaj jako prezentu",
      },
    };
  },
  components: { MyHeader },
  methods: {
    submitForm() {
      alert("Wysłano formularz!");
    },
  },
};
</script>
<!------------------------------------------------------------------------------------------------------------------------------------------------------->

<style scoped>
</style>
