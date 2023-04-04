<template>
  <div class="ui message" :class="type" v-if="!hidden">
    <i class="close icon" @click="hideNotification"></i>
    <div class="header">
      {{ header }}
    </div>
    <slot></slot>
  </div>
</template>

<script>
import "semantic-ui-css/semantic.min.css";

export default {
  props: {
    type: {
      type: String,
      default: "info",
      required: true,
    },
    header: {
      type: String,
      default: "Default Header",
      required: true,
    },
  },
  data() {
    return {
      hidden: false,
    };
  },
  methods: {
    hideNotification() {
      this.hidden = true;
    },
  },
};
</script>