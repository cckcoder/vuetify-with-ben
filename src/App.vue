<template>
  <v-app>
    <v-card width="400" class="mx-auto my-auto">
      <v-card-title>
        <h1 class="display-1">Login</h1>
      </v-card-title>
      <v-card-text>
        <v-form>
          <v-text-field 
            label="Username"
            prepend-icon="mdi-account-circle"
          />
          <v-text-field 
            :type="showPassword ? 'text' : 'Password'"
            label="Password"
            prepend-icon="mdi-lock"
            :append-icon="passEyeIcon"
            @click:append="toggleShowPassword"
          />
        </v-form>
      </v-card-text>
      <v-divider></v-divider>
      <v-card-actions>
        <v-btn color="success">Register</v-btn>
        <v-spacer></v-spacer>
        <v-btn color="info">Login</v-btn>
      </v-card-actions>
    </v-card>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  components: {
  },

  data: () => ({
    showPassword: false
  }),
  methods: {
    toggleShowPassword () {
      this.showPassword = !this.showPassword
    }
  },
  computed: {
    passEyeIcon () {
      return (this.showPassword) ? 'mdi-eye' : 'mdi-eye-off'
    }
  },

};
</script>
