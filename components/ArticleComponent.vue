<template>
  <v-card
    class="mx-auto typo-1"
    max-width="300"
    style="border-radius: 12px"
  >
    <v-img
      class="white--text align-end"
      height="204px"
      :src="image"
    >
    </v-img>

    <v-card-subtitle class="pb-0" style="font-weight: 800; font-size: 18px;">
      {{ title }}
    </v-card-subtitle>

    <v-card-text style="font-size: 14px; padding-top: 10px;">
      {{ content }}
    </v-card-text>

    <v-card-actions>
      <v-btn
        color="orange"
        text
      >
        ver más
      </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  name: 'ArticleComponent',
  props: ['title', 'content', 'image']
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
