<template>
 <v-container fluid fill-height>
        <v-layout align-center justify-center>
          <v-flex xs12 sm8 md4>
            <v-card class="elevation-12">
              <v-toolbar dark color="primary">
                <v-toolbar-title>Regestration form</v-toolbar-title>
              </v-toolbar>
              <v-card-text>
                <v-form ref="form" v-model="valid" validation>
                  <v-text-field
                    prepend-icon="person"
                    name="email"
                    label="Email"
                    :rules="emailRules"
                    type="email"
                    v-model="email"
                  ></v-text-field>
                  <v-text-field
                    prepend-icon="lock"
                    name="password"
                    label="Password"
                    :rules='passwordRules'
                    type="password"
                    v-model="password"
                    :counter="6"
                  ></v-text-field>
                   <v-text-field
                    prepend-icon="lock"
                    name="confirm-password"
                    label="Confirm password"
                    :rules='confirmPasswordRules'
                    type="password"
                    v-model="confirmPassword"
                    :counter="6"
                  ></v-text-field>
                </v-form>
              </v-card-text>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn
                 color="primary"
                 :disabled="!valid"
                 @click="onSubmit"
                >Create account</v-btn>
              </v-card-actions>
            </v-card>
          </v-flex>
        </v-layout>
</v-container>
</template>

<script>
export default {
  data () {
    return {
      email: '',
      password: '',
      confirmPassword: '',
      valid: false,
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+/.test(v) || 'E-mail must be valid'],
      passwordRules: [
        v => !!v || 'Password is required',
        v => (v && v.length >= 6) || 'Password must be equal or more than 6 characters'
      ],
      confirmPasswordRules: [
        v => !!v || 'Password is required',
        v => v === this.password || 'Password doesn`t match'
      ]
    }
  },
  methods: {
    onSubmit () {
      if (this.$refs.form.validate()) {
        const user = {
          email: this.email,
          password: this.password
        }
        console.log(user)
      }
    }
  }
}
</script>
