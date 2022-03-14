<template>
  <v-form
    ref="form"
    v-model="valid"
    lazy-validation
    @submit.prevent="submit"
  >
    <v-container class="typo-1">
      <v-row align="center" align-content="center">
        <v-col cols="6">
          <div style="flex-direction: column; width: 300px">
            <div style="font-size: 13px; font-weight: 700;">Nombre</div>
            <v-text-field
              v-model="form.name"
              :rules="rules"
              outlined
              hide-details="auto"
              style="margin-top: 10px;"
              color="#D8AD3D"
              required
            />
          </div>
        </v-col>

        <v-col cols="6">
          <div style="flex-direction: column; width: 300px">
            <div style="font-size: 13px; font-weight: 700;">Apellido</div>
            <v-text-field
            v-model="form.lastName"
              :rules="rules"
              outlined
              hide-details="auto"
              style="margin-top: 10px;"
              color="#D8AD3D"
              required
            />
          </div>
        </v-col>

        <v-col cols="6">
          <div style="flex-direction: column; width: 300px">
            <div style="font-size: 13px; font-weight: 700;">Mail</div>
            <v-text-field
            v-model="form.email"
              :rules="rules"
              outlined
              hide-details="auto"
              style="margin-top: 10px;"
              color="#D8AD3D"
              required
            />
          </div>
        </v-col>

        <v-col cols="6">
          <div style="flex-direction: column; width: 300px">
            <div style="font-size: 13px; font-weight: 700;">Telefono</div>
            <v-text-field
            v-model="form.phone"
              :rules="rules"
              outlined
              hide-details="auto"
              style="margin-top: 10px;"
              color="#D8AD3D"
              required
            />
          </div>
        </v-col>

        <v-col>
          <v-container class="d-flex align-end flex-column" style="width: 100%">
            <v-btn
              color="#D8AD3D"
              elevation="2"
              large
              style="color: white"
              @click="submit"
              type="submit"
            >Enviar</v-btn>
          </v-container>
        </v-col>

      </v-row>
    </v-container>
  </v-form>
</template>

<script>
export default {
  name: 'FormularioComponent',
  data () {
    return {
      rules: [
        value => !!value || 'Required.',
        value => (value && value.length >= 3) || 'Min 3 characters'
      ],
      form: {
        name: '',
        lastName: '',
        email: '',
        phone: ''
      },
      valid: true,
      send: false
    }
  },
  methods: {
    async submit () {
      this.$refs.form.validate()
      if (!this.valid) { return }
      await this.$axios.post('newsletter', this.form).then((response) => {
        console.log(response)
        this.send = true
      }).catch((error) => {
        console.log(error)
      })
    }
  }
}
</script>

<style lang="scss" scoped>

@import url('https://fonts.googleapis.com/css2?family=Caveat:wght@400;700&family=Open+Sans:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400;1,500;1,600&display=swap');
.typo-1 {
  //styleName: P/14;
  font-family: Open Sans;
  font-size: 14px;
  font-style: normal;
  font-weight: 400;
  line-height: 24px;
  letter-spacing: 0em;
  text-align: left;
}

</style>
