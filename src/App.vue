<template>
  <h1>{{ title }}</h1>
  <p>Welcome...</p>
  <!-- <input type="text" ref="name" /> -->
  <!-- <button @click="handleClick">Click Me</button> -->

  <!-- header="Sign up for the Giveaway!"
    text="Grab your ninja swag for half price!" -->
  <!-- <Modal :header="header" :text="text" theme="sale" /> -->

  <teleport to=".modals" v-if="showModal">
    <Modal theme="sale" @close="toggleModal">
      <template v-slot:links>
        <a href="#">signup now</a>
        <a href="#">more info</a>
      </template>
      <h1>Ninja Giveaway2</h1>
      <p>Grab your ninja swag for half price!</p>
    </Modal>
  </teleport>

  <teleport to=".modals" v-if="showModalTwo">
    <Modal @close="toggleModalTwo">
      <h1>Sign up tp the news letter</h1>
      <p>For Updates and Promo Codes</p>
    </Modal>
  </teleport>

  <button @click.alt="toggleModal">Open Modal (alt)</button>
  <button @click="toggleModalTwo">Open Modal Two</button>
</template>

<script>
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: { Modal },
  data() {
    return {
      title: "My First Vue App :)",
      header: "Sign up for the Giveaway!!!",
      text: "Grab your ninja swag for half price!",
      showModal: false,
      showModalTwo: false,
    };
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name);
      this.$refs.name.classList.add("active");
      this.$refs.name.focus();
    },

    toggleModal() {
      this.showModal = !this.showModal;
    },

    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo;
    },
  },
};
</script>

<style>
#app .modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
