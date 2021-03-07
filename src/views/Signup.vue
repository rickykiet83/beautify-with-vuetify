<template>
  <v-container class="">
    <v-row>
      <v-col>
        <h1>Signup</h1>
        <v-form ref="signupForm" v-model="formValidity">
          <v-text-field
            type="email"
            error-count=""
            placeholder="Email"
            label=""
            append-icon=""
            v-model="email"
            required
            :rules="emailRules"
          ></v-text-field>
          <v-autocomplete
            label="Which browser do you use?"
            :items="browsers"
          ></v-autocomplete>
          <v-file-input
            accept="image/*"
            label="Attach profile picture"
          ></v-file-input>
          <v-text-field
            type="text"
            error-count=""
            placeholder="Birthday"
            label="Birthday"
            append-icon=""
            v-model="birthday"
            readonly
            color
          ></v-text-field>
          <v-date-picker v-model="birthday"></v-date-picker>
          <v-checkbox
            label="Agree to terms & conditions"
            v-model="agreeToTerms"
            :rules="agreeToTermsRules"
            required
          ></v-checkbox>
          <v-btn
            class="mr-4"
            type="submit"
            color="primary"
            :disabled="!formValidity"
            >Submit</v-btn
          >
          <v-btn class="mr-4" color="success" @click="validateForm"
            >Validate Form</v-btn
          >

          <v-btn
            class="mr-4"
            type="button"
            color="warning"
            @click="resetValidation"
            >Reset Validation</v-btn
          >
          <v-btn type="button" color="error" @click="resetForm">Reset</v-btn>
        </v-form>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'Signup',
  data: () => ({
    formValidity: false,
    birthday: '',
    email: '',
    emailRules: [
      (value) => !!value || 'Email is required.',
      (value) => value.indexOf('@') !== 0 || 'Email should have a username.',
      (value) => value.includes('@') || 'Email should include an @ symbol.',
      (value) =>
        value.indexOf('.') - value.indexOf('@') > 1 ||
        'Email should contain a valid domain.',
      (value) =>
        value.indexOf('.') <= value.length - 3 ||
        'Email should contain a valid domain extension.'
    ],
    browsers: ['Chrome', 'Firefox', 'Safari', 'Edge', 'Brave'],
    agreeToTerms: false,
    agreeToTermsRules: [
      (value) => !!value || 'You must agree to the terms and conditions '
    ]
  }),
  methods: {
    resetForm() {
      this.$refs.signupForm.reset();
    },
    resetValidation() {
      this.$refs.signupForm.resetValidation();
    },
    validateForm() {
      this.$refs.signupForm.validate();
    }
  }
};
</script>

<style></style>
