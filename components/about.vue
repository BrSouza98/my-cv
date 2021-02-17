<template>
  <v-container class="px-5">
    <v-row class="my-4 py-5 my-divider" no-gutters>
      <h2>Oi! Eu sou o Bruno!</h2>
    </v-row>

    <v-row class="ml-3 mb-5 text-align">
      <p>
        Fã de cinema, faminto por rodízio japonês e amante da
        tecnologia, prazer! Passei os últimos anos procurando meu lugar no mundo
        digital, fui dês de designer gráfico, instrutor de informática e inglês,
        até técnico em informática e infra..., mas foi ingressando recentemente
        ao ensino superior Sistemas para Internet pela FATEC é que me
        reencontrei e me tornei um aspirante a desenvolvedor web full-stack!
      </p>

      <p>
        Escolhi começar com desenvolvimento front-end, acredito ser a melhor
        forma de encontrar boas oportunidades nesse começo. Atualmente busco
        consolidar meu back-end e conquistar minha primeira vaga como dev. Ah, e
        estou sempre aberto a novos desafios, me manda uma mensagem 😉.
      </p>
    </v-row>

    <v-row class="mt-5 py-5 my-divider">
      <h3>Habilidades</h3>
    </v-row>

    <v-row>
      <v-col v-for="skill in skills" :key="skill.subject" xl="4">
        <v-hover>
          <template #default="{ hover }">
            <v-card :elevation="hover ? 24 : 6" class="pa-5 my-card">
              <v-card-title class="justify-center align-center my-card-tile">
                <v-icon :color="skill.color">
                  {{ `mdi-${skill.icon}` }}
                </v-icon>{{ skill.subject }}
              </v-card-title>
              <v-card-text>
                {{ skill.text }}
              </v-card-text>
            </v-card>
          </template>
        </v-hover>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data () {
    return {
      skills: [
        {
          icon: 'language-html5',
          color: '#e34c26',
          subject: 'HTML5',
          text:
            'Uso correto das TAGs, escrita de template semantico, organizado e otimizado para SEO.'
        },
        {
          icon: 'language-css3',
          color: '#264de4',
          subject: 'CSS3',
          text:
            'Desenvolvimento de layout em grid-flexbox; pré-processadores Scss e Stylus; Frameworks CSS com foco em Bootstrap, Bulma e Tailwind CSS.'
        },
        {
          icon: 'language-javascript',
          color: '#f0db4f',
          subject: 'Javascript',
          text:
            'Validação de formulários; manipulação dos elementos DOM; estilização dos elementos html (CSS in JS); consumo de APIs.'
        },
        {
          icon: 'vuejs',
          color: '#42b983',
          subject: 'Vuejs',
          text:
            'Desenvolvimento front-end reativo orientado a componentes com os recursos do framework e seu ecossistema (vue-router, vuex e vue-loader).'
        },
        {
          icon: 'nuxt',
          color: '#00C58E',
          subject: 'Nuxt js',
          text:
            'Desenvolvimento rápido de apps/websites com framework avançado. SSR, PWA, ESlint e integração com principais frameworks css.'
        },
        {
          icon: 'vuetify',
          color: '#2196f3',
          subject: 'Vuetify',
          text:
            'Desenvolvimento de apps/websites em nuxtjs + vuetify, usando o material design como referencia para a construção de UI.'
        },
        {
          icon: 'pencil-ruler',
          color: '#FF8F00',
          subject: 'Designer',
          text:
            'Desenvolvimento de artes multiplataforma. Ferramentas Adobe CC: After Effects, Illustrator, InDesign, Photoshop, Premiere e XD.'
        },
        {
          icon: 'wordpress',
          color: '#0073aa',
          subject: 'WordPress',
          text:
            'Sites e plataformas digitais em wordpress, configurações manuais de temas e plugins partindo da finalidade do produto.'
        }
      ]
    }
  }
}
</script>

<style>
.text-align {
  text-align: justify;
}

.my-card {
  min-height: 100%;
  display: inline-flex;
  justify-content: center;
  align-skills: center;
}

.my-card .v-icon {
  font-size: 70px;
}

.my-divider {
  border-bottom: 1px solid;
}

.v-card__title {
  flex-direction: column;
  word-break: keep-all;
}

@media (max-width: 500px) {
  .my-card {
    display: flex;
    text-align: center;
    flex-direction: column;
  }

  .v-card__title {
    flex-direction: column;
  }
}
</style>
