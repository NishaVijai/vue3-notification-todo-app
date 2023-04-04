<template>
  <section>
    <PageLayout>
      <template #header>
        <h1>Header 1 - using named slot</h1>
      </template>

      <p>Paragraph - default slot from PageLayout</p>

      <template #footer>
        <footer>
          <p>Footer - using named slot</p>
        </footer>
      </template>
    </PageLayout>

    <NotificationMessage>
      <p>Notification with default "info"</p>
    </NotificationMessage>
    <NotificationMessage type="error" header="Error">
      <p>You must register before you can do that!</p>
    </NotificationMessage>
    <NotificationMessage type="success" header="Success">
      <p>Visit our registration page, then try again</p>
    </NotificationMessage>

    <button @click="isTodoTaskVisible = !isTodoTaskVisible" class="top-margin">
      Show Todo tasks
    </button>
    <ul v-if="isTodoTaskVisible" class="top-margin flex-container">
      <TodoTask> Cycling </TodoTask>
      <TodoTask> Cooking </TodoTask>
      <TodoTask> Shopping </TodoTask>
      <TodoTask> Cleaning </TodoTask>
    </ul>

    <br />

    <button
      @click="isTextColorInOrange = !isTextColorInOrange"
      class="top-margin"
    >
      Show input text in orange
    </button>
    <section v-if="isTextColorInOrange" class="top-margin">
      <InputTextOrange username="new user" />
    </section>
  </section>
</template>

<script>
import { defineAsyncComponent } from "vue";
import PageLayoutVue from "./components/PageLayout.vue";
import NotificationMessageVue from "./components/NotificationMessage.vue";
import TodoTaskVue from "./components/TodoTask.vue";

export default {
  name: "App",
  components: {
    PageLayout: PageLayoutVue,
    NotificationMessage: NotificationMessageVue,
    TodoTask: TodoTaskVue,
    InputTextOrange: defineAsyncComponent(() =>
      import(
        /*webpackChunkName: "UsernameOrange"*/ "./components/InputTextOrange.vue"
      )
    ),
  },
  data() {
    return {
      isTextColorInOrange: false,
      isTodoTaskVisible: false,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.top-margin {
  margin-top: 2rem;
}

.flex-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
}
</style>
