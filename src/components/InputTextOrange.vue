<template>
  <section>
    <label>
      Your name:
      <input placeholder="Type your name..." v-model="inputText" />
    </label>
    <p class="username-style top-margin" v-if="inputText.length > 0">
      Hello, {{ inputText }}!
    </p>
  </section>
</template>

<script>
export default {
  data() {
    return {
      inputText: "",
    };
  },
};
</script>

<style lang="scss" scoped>
$orange: #DCAE1D;
$fontSize: 2rem;
.username-style {
  color: $orange;
  font-size: $fontSize;
}
</style>