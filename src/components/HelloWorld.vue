<template>
  <v-form v-model="valid">
    <v-container>
      <v-row align="center"
      justify="center">

                    <img src="@/assets/img.svg" width="50%" height="50%"/>
      </v-row>
      <v-row align="center"
      justify="center">
        <v-col
          cols="0"
          md="0"
        >
          <v-text-field
            v-model="title"
            :rules="nameRules"
            :counter="10"
            label="Title of the reminder"
            required
          ></v-text-field>
        </v-col>

        <v-col
          cols="12"
          md="10"
        >

                    <v-text-field
            v-model="email"
            :rules="emailRules"
            label="E-mail"
            aria-placeholder="write your reminder"
            required
          ></v-text-field>
        </v-col>

        <v-col
          cols="12"
          md="4"
        >

              <v-textarea
              v-model="content"
      name="input-7-1"
      filled
      label="Label"
      auto-grow
      value="The Woodman set to work at once, and so sharp was his axe that the tree was soon chopped nearly through."
      required
    ></v-textarea>
        </v-col>
      </v-row>
    </v-container>
  </v-form>
</template>

<script>
  export default {
    data: () => ({
      valid: false,
      title: '',
      content: '',
      nameRules: [
        v => !!v || 'Name is required',
      ],
      email: '',
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+/.test(v) || 'E-mail must be valid',
      ],
    }),
  }
</script>