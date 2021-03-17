<template>
<div>
  <form>
    <label for="in">Input numbers separated by space </label>
    <input
        type="text"
        v-on:input="currentInput = $event.target.value"
        name="in"
      />
  </form>
  <button v-on:click="closerToZero()">Launch</button>
  <p>{{ res }}</p>
</div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      //result of the function and what is displayed on once the function is done
      res: "",
      //Input for the function
      currentInput: "",
    };
  },
  methods: {
    //function which take a list of valur provided by the input field
    //return a value to diplay, the closest to zero in the list given as input
    closerToZero() {
      //Filter used to clear any none number instances in the given list
      const arr = this.currentInput
        .split(" ")
        .filter((elem) => parseInt(elem) == elem);
      //checking if the list of value is empty or null
      if (arr.length === 0) {
        this.res = 0;
      } else {
        this.res = arr[0];
        //Iterating throught the values and selecting the closest to zero as we go.
        arr.forEach((element) => {
          if (
            Math.abs(element) < Math.abs(this.res) ||
            Number(element) === Math.abs(this.res)
          ) {
            this.res = element;
          }
        });
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
