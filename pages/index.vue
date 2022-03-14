<template>
  <v-row>
    <v-col cols="12" sm="12" md="12">
      <div style="position: relative;" class="typography-1">
        <v-img
          height="100vh"
          width="100vw"
          src="hero.png"
        />
        <div style="position: absolute; left: 0; top: 30px; font-size: 50px; padding: 20px 100px; font-size: 85px">
          logo
        </div>
        <div style="position: absolute; left: 0; top: 40%; font-size: 50px; padding: 20px 100px; z-index: 9; width: 635px; font-size: 85px; line-height: 70px;">
          El secreto de tu cocina
        </div>
        <v-img
          src="brush1.png"
          style="position: absolute; top: 50%; left:-500px; width: 1312px; height: 174px; z-index: 1;"
        />
        <div class="bg-image" style="position: absolute; bottom: 0; left: 0; z-index: 99; height: 150px; width:100%" />
      </div>

      <div class="text-center" style="position: relative">
        <div class="typography-1 text-center" style="font-size: 80px">
          Nuestros artículos
        </div>
        <v-row align="center" align-content="center" justify="center">
          <v-img
            src="brush2.svg"
            style="position: relative; width: 464px; max-width: 464px; top: -55px"
          />
        </v-row>
      </div>

      <div style="flex-direction: row;">

        <div style="width: 300px;">
          <div class="card-style">
              <div style="flex-direction: row; color: #D8AD3D;">
                <label style="width: auto">TODOS</label>
                <v-icon
                  color="#D8AD3D"
                >mdi-arrow-right</v-icon>
              </div>
              <div style="margin-top: 20px">PRODUCTOS</div>
              <div style="margin-top: 20px">RECETAS</div>
              <div style="margin-top: 20px">CONSEJOS</div>
            </div>
        </div>

        <div style="flex-direction: row; padding: 20px; margin-top: 20px">
          <v-row>
            <ArticleComponent
              v-for="(item, ind) in data"
              :key="ind"
              v-bind="item"
              style="margin-top: 20px"
            />
          </v-row>
        </div>

      </div>

      <div class="text-center" style="position: relative; margin-top: 50px">
        <div class="typography-1 text-center" style="font-size: 80px">
          Contáctanos
        </div>
        <v-row align="center" align-content="center" justify="center">
          <v-img
            src="brush2.svg"
            style="position: relative; width: 464px; max-width: 464px; top: -55px"
          />
        </v-row>
      </div>

      <v-container>
        <FormularioComponent />
      </v-container>
    </v-col>
  </v-row>
</template>

<script>
import ArticleComponent from '~/components/ArticleComponent.vue'
import FormularioComponent from '~/components/FormularioComponent.vue'
export default {
  name: 'IndexPage',
  components: { ArticleComponent, FormularioComponent },
  data () {
    return {
      data: []
    }
  },
  mounted () {
    this.getItems()
  },
  methods: {
    async getItems () {
      await this.$axios.get('/articles?filter=Productos').then((response) => {
        console.log(response)
        this.data = response.data
      })
    }
  }
}
</script>

<style lang="scss" scoped>

@import url('https://fonts.googleapis.com/css2?family=Caveat:wght@400;700&display=swap');

.bg-image {
  background: linear-gradient(180deg, rgba(253, 253, 253, 0.015) 0%, rgba(255, 255, 255, 0.659) 37%, rgb(255, 255, 255) 100%);
}

.typography-1 {
  font-family: Caveat;
  font-style: normal;
  font-weight: 700;
  letter-spacing: 0em;
  text-align: left;
}

.text-center {
  text-align: center;
}

.card-style {
  width: 274px;
  height: 319px;
  left: 131px;
  top: 966px;
  margin-left: 10px;
  padding: 20px;

  background: #FFFFFF;
  /* shadow box */

  box-shadow: 0px 4px 40px rgba(0, 0, 0, 0.07);
  border-radius: 10px;
  flex-direction: column;
}

</style>
