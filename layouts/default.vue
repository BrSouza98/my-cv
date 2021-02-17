<template>
  <v-app dark>
    <v-navigation-drawer v-model="drawer" app>
      <v-img
        lazy-src="https://avatars.githubusercontent.com/u/61894533?s=400&u=068277645e0eb6b6984565bde5be8fea3bc1f5da&v=4"
        height="300"
        src="https://avatars.githubusercontent.com/u/61894533?s=400&u=068277645e0eb6b6984565bde5be8fea3bc1f5da&v=4"
        class="ma-2 rounded-lg"
        elevation="3"
      />
      <v-card max-width="400" class="ma-2 rounded" elevation="3">
        <v-card-title class="text-center d-block ma-2">
          <h3>Bruno Souza</h3>
        </v-card-title>

        <v-divider />

        <v-list two-line>
          <v-list-item v-for="info in infos" :key="info.title" two-line>
            <v-list-item-icon>
              <v-icon> mdi-{{ info.icon }} </v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title> {{ info.title }}</v-list-item-title>
              <v-list-item-subtitle>{{ info.text }}</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
        </v-list>

        <v-divider class="pa-2 ma-2" inset />

        <v-list-item v-for="hireme in hiremes" :key="hireme.title" two-line>
          <v-list-item-icon>
            <v-icon> mdi-{{ hireme.icon }} </v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title> {{ hireme.title }}</v-list-item-title>
            <v-list-item-subtitle>{{ hireme.text }}</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </v-card>
      <v-row class="d-flex justify-center mt-5">
        <v-btn
          color="primary"
          elevation="3"
          class="mx-2"
          large
          href="https://drive.google.com/file/d/1HxkzyyxWUNIBJRuvlGfoGiqj1Od9cLNQ/view?usp=sharing"
          target="_blank"
        >
          Curriculo/CV
          <v-icon right>
            far fa-file-pdf
          </v-icon>
        </v-btn>
      </v-row>
    </v-navigation-drawer>

    <v-app-bar class="justify-space-between" app>
      <v-app-bar-nav-icon class="d-lg-none" @click="drawer = true" />
      <v-tabs v-model="tabs" color="primary" centered>
        <v-tab v-for="item in items" :key="item.page">
          {{ item.page }}
        </v-tab>
      </v-tabs>
      <div class="d-flex justify-end">
        <v-btn icon href="https://github.com/BrSouza98" target="_blank">
          <v-icon class="ma-2">
            fab fa-github
          </v-icon>
        </v-btn>
        <v-btn icon href="https://www.linkedin.com/in/bruno-silva-91382b170/" target="_blank">
          <v-icon class="ma-2">
            fab fa-linkedin
          </v-icon>
        </v-btn>
      </div>
    </v-app-bar>

    <v-content>
      <v-container>
        <v-tabs-items v-model="tabs" class="rounded-lg ma-5 pa-5" elevation-1>
          <v-tab-item>
            <LazyAbout />
          </v-tab-item>

          <v-tab-item>
            <LazyJobs />
          </v-tab-item>

          <v-tab-item>
            <LazyHireme />
          </v-tab-item>
        </v-tabs-items>
      </v-container>

      <v-btn
        class="light-button mx-2"
        fab
        x-large
        color="accent"
        @click="$vuetify.theme.dark = !$vuetify.theme.dark"
      >
        <v-icon v-model="$vuetify.theme.dark">
          mdi-theme-light-dark
        </v-icon>
      </v-btn>
    </v-content>
  </v-app>
</template>

<script>
import '@fortawesome/fontawesome-free/css/all.css'

export default {
  data () {
    return {
      tabs: null,
      items: [{ page: 'Sobre' }, { page: 'Projetos' }, { page: 'Contato' }],

      infos: [
        { title: '22 Anos', text: '15/09/1998', icon: 'cake' },
        { title: 'Ensino Superior', text: 'Conclusão em 2022', icon: 'school' },
        { title: 'Objetivo', text: 'Desenvolvimento Web', icon: 'web' }
      ],

      hiremes: [
        { title: 'Telefone', text: '(16) 99104-6172', icon: 'phone' },
        { title: 'Comercial', text: '(16) 99991-2369', icon: 'phone' },
        { title: 'Gmail', text: 'brunosouza002bs', icon: 'email' }
      ],

      drawer: true,
      group: null
    }
  }
}
</script>

<style lang="scss" scoped>
.light-button {
  position: fixed;
  bottom: 30px;
  right: 30px;
}
</style>
