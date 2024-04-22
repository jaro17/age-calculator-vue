<script>
export default {
  name: "Calculator",
  data() {
    return {
      birthday: "",
    }
  },
  methods: {
    calculateAge() {
      if (!this.birthday) {
        alert("Please enter a valid birthday")
        return;
      }

      const currentDate = new Date();
      const birthdayDate = new Date(this.birthday);
      let age = currentDate.getFullYear() - birthdayDate.getFullYear();
      const month = currentDate.getMonth() - birthdayDate.getMonth();

      if (month < 0 || (month === 0 && currentDate.getDate() < birthdayDate.getDate())) {
        age--;
      }

      const resultParagraph = this.$refs.resultParagraph;
      resultParagraph.innerText = `You are ${age} ${age > 1 ? "years" : "year"} old`;
    },


  }
}
</script>

<template>
  <div class="container">
    <div class="card has-text-centered">
      <h1 class="is-size-3 has-text-weight-semibold">Age Calculator</h1>
      <div class="form">
        <label for="birthday" class="mt-4">Enter your date of birth</label>
        <input type="date" v-model="birthday" id="birthday" name="birthday">
        <button @click="calculateAge" class="button is-link" >Calculate Age</button>
        <p class="result is-size-4 has-text-weight-bold" ref="resultParagraph"></p>
      </div>
    </div>
  </div>
</template>

<style>
@import "https://cdn.jsdelivr.net/npm/bulma@1.0.0/css/bulma.min.css";

.card {
  width: 30rem;
  margin: 5rem auto;
  padding-top: 2rem;
  padding-bottom: 2rem;
}

.form {
  display: flex;
  flex-direction: column;
  align-items: center;
}

input[type="date"] {
  width: 60%;
  margin-top: 1rem;
  padding: 3px;
  border-radius: 5px;
}

.button, p {
  margin-top: 1rem;
}

</style>