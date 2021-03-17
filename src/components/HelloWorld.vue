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
    msg: String
  },
   data() {
    return {
      res: '',
      currentInput: ''
    };
  },
   methods: {
    closerToZero() {
      const arr = this.currentInput.split(" ").filter(elem => (parseInt(elem) == elem));
      if (arr.length === 0) {
         this.res = 0;
      }
      else{
        this.res = arr[0];
        arr.forEach(element => {
          if ( Math.abs(element) < Math.abs(this.res) || Number(element) === Math.abs(this.res) ) {
            this.res = element
          }
        });
      }
    }
  }
};

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
