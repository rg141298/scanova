<template>
  <div>
    <v-card v-if="show1" class="mx-auto my-12" max-width="374">
      <v-img
        height="250"
        src="https://cdn.vuetifyjs.com/images/cards/cooking.png"
      ></v-img>
      <v-card-title>Card Title</v-card-title>
      <v-card-actions class="cardText">
        <div>
          Some quick example text to build on the card<br />
          &nbsp;&nbsp;&nbsp;&nbsp; title and make up the bulk of the card's
          content.
        </div>
      </v-card-actions>
      <v-card-text>
        <v-btn class="button" @click="button()">BUTTON</v-btn>
      </v-card-text>
    </v-card>

    <v-card v-if="show2" class="mx-auto my-12" max-width="374">
      <v-img
        height="250"
        src="https://cdn.vuetifyjs.com/images/cards/cooking.png"
      ></v-img>
      <v-card-title>Welcome</v-card-title>
      <v-card-actions class="cardText">
        <div>Thank you for your action. We will get in touch<br />shortly</div>
      </v-card-actions>
      <v-card-text>
        <v-btn class="back" @click="back()">BACK</v-btn>
      </v-card-text>
    </v-card>
  </div>
</template>

<script>
export default {
  data: () => ({
    show1: true,
    show2: false,
  }),

  mounted() {},
  methods: {
    button() {
      this.show2 = true;
      this.show1 = false;
    },
    back() {
      this.show1 = true;
      this.show2 = false;
    },
  },
};
</script>

<style>
.button {
  background-color: blueviolet !important;
  color: white !important;
}
.back {
  background-color: deeppink !important;
  color: white !important;
}
.cardText {
  text-align: left;
  color: grey;
}
</style>
