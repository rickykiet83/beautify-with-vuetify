<template>
  <v-container class="">
    <v-row>
      <v-col>
        <h1>Signup</h1>
        <v-form>
          <v-text-field
            type="email"
            error-count=""
            placeholder="Email"
            label=""
            append-icon=""
            v-model="email"
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
          <v-checkbox label="Agree to terms & conditions"></v-checkbox>
          <v-btn type="submit" color="primary">Submit</v-btn>
        </v-form>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'Signup',
  data: () => ({
    birthday: '',
    browsers: ['Chrome', 'Firefox', 'Safari', 'Edge', 'Brave']
  })
};
</script>

<style></style>
