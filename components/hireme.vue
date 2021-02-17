<template>
  <v-container>
    <h2 class="headline">
      <span
        style="border-bottom: 1px solid"
      >Precisando falar co</span>migo?
    </h2>
    <validation-observer ref="observer" v-slot="{ invalid }">
      <form @submit.prevent="submit">
        <v-row class="my-5">
          <v-col cols="12" md="6" lg="6" xl="6">
            <validation-provider
              v-slot="{ errors }"
              name="nome"
              rules="required|max:40"
            >
              <v-text-field
                v-model="name"
                :counter="40"
                :error-messages="errors"
                label="Nome"
                required
              />
            </validation-provider>
          </v-col>
          <v-col>
            <validation-provider
              v-slot="{ errors }"
              name="email"
              rules="required|email|"
            >
              <v-text-field
                v-model="email"
                :error-messages="errors"
                label="E-mail"
                required
              />
            </validation-provider>
          </v-col>
        </v-row>
        <v-text-field
          v-model="title"
          label="Assunto"
          single-line
          full-width
          hide-details
          outlined
        />
        <v-textarea
          v-model="message"
          label="Mensagem"
          counter
          outlined
          maxlength="120"
          full-width
          single-line
        />

        <v-row>
          <v-col>
            <v-btn class="mr-4" color="success" type="submit" :disabled="invalid">
              submit
            </v-btn>
            <v-btn color="error" outlined @click="clear">
              clear
            </v-btn>
          </v-col>
        </v-row>
      </form>
    </validation-observer>
  </v-container>
</template>

<script>
import { required, digits, email, max, regex } from 'vee-validate/dist/rules'
import {
  extend,
  ValidationObserver,
  ValidationProvider,
  setInteractionMode
} from 'vee-validate'

setInteractionMode('eager')

extend('digits', {
  ...digits,
  message: 'Seu {_field_} precisa ter {length} digitos. ({_value_})'
})

extend('required', {
  ...required,
  message: 'O campo {_field_} precisa ser preenchido'
})

extend('max', {
  ...max,
  message: '{_field_} may not be greater than {length} characters'
})

extend('regex', {
  ...regex,
  message: '{_field_} {_value_} does not match {regex}'
})

extend('email', {
  ...email,
  message: 'Email must be valid'
})

export default {
  components: {
    ValidationProvider,
    ValidationObserver
  },
  data: () => ({
    name: '',
    phoneNumber: '',
    email: '',
    text: ''
  }),

  methods: {
    submit () {
      this.$refs.observer.validate()
    },
    clear () {
      this.name = ''
      this.phoneNumber = ''
      this.email = ''
      this.$refs.observer.reset()
    }
  }
}
</script>

<style>
</style>
