<template>
  <v-form ref="form" v-models="valid" lazy-validation>
    <v-img  src='http://www.rhcompetence.com/wp-content/uploads/2019/03/Biblioth%C3%A8que-en-Ligne.jpg'></v-img>
    <v-text-field
      v-model="Firstname"
      :counter="10"
      :rules="FirstnamenameRules"
      label="FirstName"
      required
    ></v-text-field>

    <v-text-field v-model="name" :counter="10" :rules="nameRules" label="Name" required></v-text-field>
    <v-text-field
      v-model="StudentNumber"
      :rules="StudentNumberRules"
      label="StudentNumber"
      required
    ></v-text-field>
    <v-text-field v-model="email" :rules="emailRules" label="E-mail" required></v-text-field>

    <v-checkbox
      v-model="checkbox"
      :rules="[v => !!v || 'You must agree to continue!']"
      label="Do you agree?"
      required
    ></v-checkbox>

    <v-btn :disabled="!valid" color="success" class="mr-4" @click="validate">Validate</v-btn>

    <v-btn color="error" class="mr-4" @click="restart">restart</v-btn>

    <v-btn color="warning" @click="Quit">Quit</v-btn>

  </v-form>
</template>

<script>
export default {
  data: () => ({
    valid: true,
    Firstname: '',
    FirstnameRules: [
      v => !!v || 'FirstName is required',
      v => (v && v.length <= 10) || 'FisrtName must be less than 10 characters'
    ],
    name: '',
    nameRules: [
      v => !!v || 'Name is required',
      v => (v && v.length <= 10) || 'Name must be less than 10 characters'
    ],
    StudentNumber: '',
    StudentNumberlRules: [
      v => !!v || 'StudentNumber is required',
      v => /.+@.+\..+/.test(v) || 'StudentNumber must be valid'
    ],
    email: '',
    emailRules: [
      v => !!v || 'E-mail is required',
      v => /.+@.+\..+/.test(v) || 'E-mail must be valid'
    ]
  }),

  methods: {
    validate () {
      if (this.$refs.form.validate()) {
        this.snackbar = true
      }
    },
    restart () {
      this.$refs.form.restart()
    },
    Quit () {
      this.$refs.form.Quit()
    }
  }
}
</script>
