<template>
  <v-container >
    <v-layout row align-center justify-center>
      <v-flex>
        <v-card light>
          <v-card-title>
            Registrate
          </v-card-title>
            <form>
              <v-text-field
                v-model="name"
                :error-messages="nameErrors"
                :counter="50"
                label="Nombre"
                required
                @input="$v.name.$touch()"
                @blur="$v.name.$touch()"
              ></v-text-field>
              <v-text-field
                v-model="email"
                :error-messages="emailErrors"
                label="Correo Electronico"
                required
                @input="$v.email.$touch()"
                @blur="$v.email.$touch()"
              ></v-text-field>
              <v-select
                v-model="select"
                :items="items"
                :error-messages="selectErrors"
                label="Semestre"
                required
                @change="$v.select.$touch()"
                @blur="$v.select.$touch()"
              ></v-select>
              <v-checkbox
                v-model="checkbox"
                :error-messages="checkboxErrors"
                label="¿Aceptas los terminos y condiciones?"
                required
                @change="$v.checkbox.$touch()"
                @blur="$v.checkbox.$touch()"
              ></v-checkbox>

              <v-btn @click="submit">Registrate</v-btn>
              <v-btn @click="clear">Limpiar</v-btn>
            </form>
        </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
  
  import { validationMixin } from 'vuelidate'
  import { required, maxLength, email } from 'vuelidate/lib/validators'

  export default {
    mixins: [validationMixin],

    validations: {
      name: { required, maxLength: maxLength(50) },
      email: { required, email },
      select: { required },
      checkbox: {
        checked (val) {
          return val
        }
      }
    },

    data: () => ({
      name: '',
      email: '',
      select: null,
      items: [
        'Primer Semestre',
        'Segundo Semestre',
        'Tercer Semestre',
        'Cuarto Semestre',
        'Quinto Semestre',
        'Sexto Semestre'
      ],
      checkbox: false
    }),

    computed: {
      checkboxErrors () {
        const errors = []
        if (!this.$v.checkbox.$dirty) return errors
        !this.$v.checkbox.checked && errors.push('Tienes que aceptar para continuar!')
        return errors
      },
      selectErrors () {
        const errors = []
        if (!this.$v.select.$dirty) return errors
        !this.$v.select.required && errors.push('Selecciona un Semestre')
        return errors
      },
      nameErrors () {
        const errors = []
        if (!this.$v.name.$dirty) return errors
        !this.$v.name.maxLength && errors.push('El nombre debe ser de maximo 15 caracteres')
        !this.$v.name.required && errors.push('Es necesario tu nombre.')
        return errors
      },
      emailErrors () {
        const errors = []
        if (!this.$v.email.$dirty) return errors
        !this.$v.email.email && errors.push('Introduce un e-mail correcto')
        !this.$v.email.required && errors.push('Es necesario un e-mail')
        return errors
      }
    },

    methods: {
      submit () {
        this.$v.$touch()
      },
      clear () {
        this.$v.$reset()
        this.name = ''
        this.email = ''
        this.select = null
        this.checkbox = false
      }
    }
  }
</script>
