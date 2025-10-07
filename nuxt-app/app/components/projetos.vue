<template>
  <div class="projetos-container">
    <div class="projetos-header">
      <h1 class="titulo-projetos">MEUS PROJETOS</h1>
      <p class="subtitulo-projetos">Explore alguns dos projetos que desenvolvi utilizando diferentes tecnologias</p>
    </div>

    <v-container>
      <v-row>
        <v-col cols="12" md="6" lg="4" v-for="projeto in projetos" :key="projeto.id">
          <v-card class="projeto-card" elevation="8" hover>
            <div class="card-header">
              <v-icon :icon="projeto.icone" size="48" class="projeto-icone"></v-icon>
            </div>

            <v-card-title class="projeto-titulo">
              {{ projeto.nome }}
            </v-card-title>

            <v-card-subtitle class="projeto-categoria">
              {{ projeto.categoria }}
            </v-card-subtitle>

            <v-card-text class="projeto-descricao">
              {{ projeto.descricao }}
            </v-card-text>

            <div class="linguagens-section">
              <div class="linguagens-badges">
                <v-chip v-for="linguagem in projeto.linguagens" :key="linguagem.nome" :color="linguagem.cor"
                  size="small" class="linguagem-chip">
                  <v-icon :icon="linguagem.icone" size="16" class="mr-1"></v-icon>
                  {{ linguagem.nome }}
                </v-chip>
              </div>
            </div>

            <v-card-actions class="card-actions">
              <v-btn :href="projeto.github" target="_blank" variant="outlined" color="primary" class="action-btn">
                <v-icon icon="mdi-github" class="mr-2"></v-icon>
                Código
              </v-btn>
              <v-btn v-if="projeto.demo" :href="projeto.demo" target="_blank" variant="flat" color="primary"
                class="action-btn">
                <v-icon icon="mdi-open-in-new" class="mr-2"></v-icon>
                Demo
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const projetos = ref([
  {
    id: 1,
    nome: 'DevLinks',
    categoria: 'Landing Page',
    descricao: 'Agregador de links para usar como cartão de visitas online. Projeto desenvolvido durante programa da Rocketseat para ensino de tecnologias WEB.',
    linguagens: [
      { nome: 'CSS', cor: 'blue', icone: 'mdi-language-css3' },
      { nome: 'HTML', cor: 'orange', icone: 'mdi-language-html5' },
      { nome: 'JS', cor: 'yellow', icone: 'mdi-language-javascript' }
    ],
    icone: 'mdi-link-variant',
    github: 'https://github.com/Matheus-Lino/projeto-pagina-de-links',
    demo: null
  },
  {
    id: 2,
    nome: 'Calculadora Dinâmica',
    categoria: 'Aplicação Web',
    descricao: 'Calculadora interativa desenvolvida em JavaScript puro, focada em lógica de programação e manipulação do DOM.',
    linguagens: [
      { nome: 'HTML', cor: 'orange', icone: 'mdi-language-html5' },
      { nome: 'JS', cor: 'yellow', icone: 'mdi-language-javascript' }
    ],
    icone: 'mdi-calculator',
    github: 'https://github.com/Matheus-Lino/Calculadora-Din-mica-',
    demo: null
  },
  {
    id: 3,
    nome: 'Projeto Vue.js 3',
    categoria: 'Framework Frontend',
    descricao: 'Projeto desenvolvido para explorar as funcionalidades e recursos do Vue.js 3, incluindo Composition API e reatividade.',
    linguagens: [
      { nome: 'Vue', cor: 'green', icone: 'mdi-vuejs' },
      { nome: 'JS', cor: 'yellow', icone: 'mdi-language-javascript' }
    ],
    icone: 'mdi-vuejs',
    github: 'https://github.com/Matheus-Lino/Projeto_Vue.js3',
    demo: null
  },
  {
    id: 4,
    nome: 'Curso Vue.js 3',
    categoria: 'Projeto de Estudos',
    descricao: 'Aplicação prática dos conceitos aprendidos no curso de Vue.js 3, demonstrando componentes, roteamento e gerenciamento de estado.',
    linguagens: [
      { nome: 'Vue', cor: 'green', icone: 'mdi-vuejs' },
      { nome: 'JS', cor: 'yellow', icone: 'mdi-language-javascript' }
    ],
    icone: 'mdi-school',
    github: 'https://github.com/Matheus-Lino/CursoVue.js3',
    demo: null
  },
  {
    id: 5,
    nome: 'Projeto Nuxt.js',
    categoria: 'Framework Full-Stack',
    descricao: 'Exploração do framework Nuxt.js para desenvolvimento de aplicações Vue.js com renderização server-side e geração estática.',
    linguagens: [
      { nome: 'Vue', cor: 'green', icone: 'mdi-vuejs' },
      { nome: 'TS', cor: 'blue', icone: 'mdi-language-typescript' }
    ],
    icone: 'mdi-nuxt',
    github: 'https://github.com/Matheus-Lino/Projeto-NuxtJS',
    demo: null
  },
  {
    id: 6,
    nome: 'Calculado IMC',
    categoria: 'Aplicação Web',
    descricao: 'A Calculadora de IMC usa HTML para os campos de entrada (peso/altura) e JavaScript para calcular (peso/altura 2) e classificar o resultado. É a união de estrutura e lógica para uma ferramenta prática.',
    linguagens: [
       { nome: 'HTML', cor: 'orange', icone: 'mdi-language-html5' },
       { nome: 'JS', cor: 'yellow', icone: 'mdi-language-javascript'}
    ],
    icone: 'mdi-calculator',
    github: 'https://github.com/Matheus-Lino/Calculadora-IMC',
    demo: null
  },
])
</script>

<style scoped>
.projetos-container {
  min-height: 100vh;
  background: linear-gradient(135deg, rgba(0, 0, 0, 0.95), rgba(25, 20, 35, 0.9));
  padding: 60px 0;
  font-family: "Bitcount Single Ink", system-ui;
}

.projetos-header {
  text-align: center;
  margin-bottom: 60px;
  padding: 0 20px;
}

.titulo-projetos {
  font-family: "Bitcount Single Ink", system-ui;
  font-size: clamp(32px, 6vw, 48px);
  font-weight: 700;
  background: linear-gradient(135deg, #8e2de2, #4a00e0);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 20px;
  letter-spacing: 2px;
}

.subtitulo-projetos {
  font-size: clamp(16px, 3vw, 20px);
  color: #b0a8c2;
  max-width: 600px;
  margin: 0 auto;
  line-height: 1.6;
}

.projeto-card {
  background: rgba(25, 20, 35, 0.85) !important;
  backdrop-filter: blur(15px);
  -webkit-backdrop-filter: blur(15px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 20px !important;
  transition: all 0.3s ease;
  height: 100%;
  display: flex;
  flex-direction: column;
}

.projeto-card:hover {
  transform: translateY(-10px) scale(1.02);
  box-shadow: 0 20px 40px rgba(142, 45, 226, 0.3) !important;
  border-color: rgba(142, 45, 226, 0.5);
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  padding: 20px 20px 0;
}

.projeto-icone {
  color: #8e2de2;
  margin-bottom: 15px;
}

.linguagens-section {
  padding: 20px;
}

.linguagens-badges {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  justify-content: center;
}

.linguagem-chip {
  font-size: 12px !important;
  height: 24px !important;
  font-family: "Inter", system-ui, sans-serif;
}

.projeto-titulo {
  color: #f5f5f5 !important;
  font-family: "Bitcount Single Ink", system-ui !important;
  font-size: 24px !important;
  font-weight: 600 !important;
  padding: 0 20px !important;
}

.projeto-categoria {
  color: #8e2de2 !important;
  font-family: "Inter", system-ui, sans-serif !important;
  font-size: 14px !important;
  font-weight: 500 !important;
  padding: 0 20px 10px !important;
}

.projeto-descricao {
  color: #c5c0d1 !important;
  font-family: "Inter", system-ui, sans-serif !important;
  line-height: 1.6 !important;
  padding: 0 20px !important;
  flex-grow: 1;
}

.card-actions {
  padding: 20px !important;
  gap: 12px;
  margin-top: auto;
}

.action-btn {
  font-family: "Inter", system-ui, sans-serif !important;
  font-weight: 500 !important;
  text-transform: none !important;
  border-radius: 25px !important;
  transition: all 0.3s ease !important;
}

.action-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(142, 45, 226, 0.4);
}

@media (max-width: 768px) {
  .projetos-container {
    padding: 40px 0;
  }

  .projetos-header {
    margin-bottom: 40px;
  }

  .card-header {
    flex-direction: column;
    align-items: flex-start;
    gap: 15px;
  }

  .linguagens-badges {
    flex-direction: row;
    align-items: flex-start;
    flex-wrap: wrap;
  }

  .card-actions {
    flex-direction: column;
  }

  .action-btn {
    width: 100%;
  }
}

@media (max-width: 480px) {
  .projeto-titulo {
    font-size: 20px !important;
  }

  .projeto-descricao {
    font-size: 14px !important;
  }
}
</style>
