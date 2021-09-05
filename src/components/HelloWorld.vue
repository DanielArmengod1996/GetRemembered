<template>
  <v-form v-model="valid">
    <v-container>
      <v-row align="center" justify="center">
        <img src="@/assets/img.svg" width="50%" height="100%"/>
      </v-row>
      <v-row align="center" justify="center">
        <v-col cols="13" md="10">
          <v-text-field v-model="title" :rules="nameRules" :counter="40" 
            label="Title of the reminder" required></v-text-field>
        </v-col>
      </v-row>

      <v-row align="center" justify="center">
        <v-col cols="13" md="10">
          <v-text-field v-model="email" :rules="emailRules" label="E-mail" 
            aria-placeholder="write your reminder" required ></v-text-field>
        </v-col>
      </v-row>
      
      <v-row align="center" justify="center">
        <v-col cols="13" md="10">
          <v-textarea v-model="content" name="input-7-1" filled label="Argument for the reminder ..." auto-grow required></v-textarea>
        </v-col>
      </v-row>

      <v-row align="center" justify="center">
        <v-col cols="13" md="10">
          Scheduled date: <input required class="mr-4" type="datetime-local" v-model="datetimescheduled" name="datetime">
        </v-col>
      </v-row>

      <v-row align="center" justify="center">
        <v-col cols="13" md="10">
          <v-btn class="mr-4" @click="submit">SCHEDULE</v-btn>
        </v-col>
      </v-row>
    </v-container>
    <!-- button for scroll to down -->
    <v-btn v-scroll="onScroll" v-show="fab" width = "50%" dark fixed block elevation="24" bottom color="none" @click="toBottom">
      <v-icon>mdi-arrow-down</v-icon>
    </v-btn>
  </v-form>
  
</template>

<script>
  export default {
    data: () => ({
      dialog: false,
      valid: false,
      fab: true,
      datetimescheduled: null,
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
    methods: {
      onScroll (e) {
        if (typeof window === 'undefined') return
        const top = window.pageYOffset ||   e.target.scrollTop || 0
        this.fab = top < 20
      },
      toBottom () {
        this.$vuetify.goTo(document.body.scrollHeight)
      }
    },
  }
</script>