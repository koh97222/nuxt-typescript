<template>
  <v-container>
    <v-card>
      <v-card-title>
        Todos
      </v-card-title>
      <v-card-text> {{ id }}さん、ようこそ </v-card-text>
      <div v-if="articles">
        <div class="mt-5"></div>
        <v-card-text style="height: 300px;" class="grey lighten-5">
          <li v-for="article in articles">
            {{ article.content }}
          </li>
        </v-card-text>
        <v-card-text style="height: 100px; position: relative">
          <v-btn absolute dark fab top right color="blue">
            <v-icon>mdi-plus</v-icon>
          </v-btn>
        </v-card-text>
      </div>
    </v-card>
  </v-container>
</template>
<style scoped></style>
<script>
export default {
  computed: {
    articles() {
      return this.todos.filter(todos => todos.id === this.id);
    }
  },
  data() {
    return {
      id: this.$route.params.id,
      todos: [
        {
          id: "hayakin",
          content: "早起きして散歩する。"
        },
        {
          id: "hayakin",
          content: "買い物へ行く。"
        },
        {
          id: "muscle",
          content: "ジムへ行く"
        }
      ]
    };
  }
};
</script>
