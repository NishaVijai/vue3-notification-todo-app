<template>
  <li class="list-style-none flex-container">
    <label class="style">
      <input name="todoItemCheckbox" type="checkbox" v-model="completed" />
      <span :class="{ completed }">
        <slot></slot>
      </span>
    </label>
  </li>
</template>

<script>
export default {
  data() {
    return {
      completed: false,
    };
  },
};
</script>

<style scoped>
.completed {
  color: green;
  text-decoration: line-through;
}

.list-style-none {
  list-style: none;
  min-width: 20vw;
}

.style {
  width: 100%;
  text-align: left;
}
</style>