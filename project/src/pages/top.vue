<template>
  <v-row :alignment="alignment" :justify="justify">
    <v-col cols="9">
      <v-card class="mx-auto" max-width="600">
        <v-card-title>OnedayOnelife</v-card-title>
        <v-spacer></v-spacer>
        <v-card-actions>
          <v-btn outlined>Login</v-btn>
          <v-btn outlined>新規登録</v-btn>
          <v-btn outlined>おためしログイン</v-btn>
        </v-card-actions>
        <v-form>
          <v-container>
            <v-row>
              <v-col cols="12" md="8">
                <v-text-field
                  v-model="id"
                  :rules="idRules"
                  :counter="10"
                  label="ID"
                  required
                ></v-text-field>
              </v-col>
              <v-col cols="12" md="4">
                <v-btn @click="transitionPage(id)">to _id.vue</v-btn>
              </v-col>
            </v-row>
          </v-container>
        </v-form>
      </v-card>
      <div class="mt-5">
        <v-data-table
          :headers="headers"
          :items="desserts"
          :items-per-page="5"
          class="elevation-1 mx-auto"
        ></v-data-table>
      </div>
    </v-col>

    <v-col cols="3">
      <v-btn outlined class="mx-2" fab dark large color="cyan">
        <v-icon dark>mdi-pencil</v-icon>
      </v-btn>
    </v-col>
  </v-row>
</template>
<style scoped></style>
<script>
export default {
  data() {
    return {
      id: "",
      idRules: [
        v => !!v || "ID is required",
        v => v.length <= 10 || "ID must be less than 10 characters"
      ],
      alignment: "center",
      justify: "center",
      headers: [
        {
          text: "Dessert (100g serving)",
          align: "start",
          sortable: false,
          value: "name"
        },
        { text: "Calories", value: "calories" },
        { text: "Fat (g)", value: "fat" },
        { text: "Carbs (g)", value: "carbs" },
        { text: "Protein (g)", value: "protein" },
        { text: "Iron (%)", value: "iron" }
      ],
      desserts: [
        {
          name: "Frozen Yogurt",
          calories: 159,
          fat: 6.0,
          carbs: 24,
          protein: 4.0,
          iron: "1%"
        },
        {
          name: "Ice cream sandwich",
          calories: 237,
          fat: 9.0,
          carbs: 37,
          protein: 4.3,
          iron: "1%"
        },
        {
          name: "Eclair",
          calories: 262,
          fat: 16.0,
          carbs: 23,
          protein: 6.0,
          iron: "7%"
        },
        {
          name: "Cupcake",
          calories: 305,
          fat: 3.7,
          carbs: 67,
          protein: 4.3,
          iron: "8%"
        },
        {
          name: "Gingerbread",
          calories: 356,
          fat: 16.0,
          carbs: 49,
          protein: 3.9,
          iron: "16%"
        },
        {
          name: "Jelly bean",
          calories: 375,
          fat: 0.0,
          carbs: 94,
          protein: 0.0,
          iron: "0%"
        },
        {
          name: "Lollipop",
          calories: 392,
          fat: 0.2,
          carbs: 98,
          protein: 0,
          iron: "2%"
        },
        {
          name: "Honeycomb",
          calories: 408,
          fat: 3.2,
          carbs: 87,
          protein: 6.5,
          iron: "45%"
        },
        {
          name: "Donut",
          calories: 452,
          fat: 25.0,
          carbs: 51,
          protein: 4.9,
          iron: "22%"
        },
        {
          name: "KitKat",
          calories: 518,
          fat: 26.0,
          carbs: 65,
          protein: 7,
          iron: "6%"
        }
      ]
    };
  },
  methods: {
    transitionPage(id) {
      this.$router.push({ path: `todo/${id}` });
    }
  }
};
</script>
