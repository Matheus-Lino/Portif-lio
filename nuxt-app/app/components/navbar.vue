<template>
    <v-app-bar class="bg-black navbar-custom" fixed>
         <v-app-bar-title class="title">Matheus Lino</v-app-bar-title>
            <v-btn id="botoes" @click="scrollToSection('sobre')">Sobre</v-btn>
            <v-btn id="botoes" @click="scrollToSection('projetos')">Projetos</v-btn>
            <v-btn id="botoes" @click="scrollToSection('contatos')">Contato</v-btn>
    </v-app-bar>
</template>

<script setup>
const scrollToSection = (sectionId) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ 
      behavior: 'smooth',
      block: 'start'
    })
  }
}
</script>

<style scoped>
.navbar-custom {
  backdrop-filter: blur(15px);
  -webkit-backdrop-filter: blur(15px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  z-index: 1000;
}

.title {
  font-family: "Bitcount Single Ink", system-ui;
  font-size: clamp(18px, 4vw, 24px);
  background: linear-gradient(135deg, #8e2de2, #4a00e0);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  font-weight: 600;
}

#botoes {
  font-family: "Bitcount Single Ink", system-ui;
  font-size: clamp(12px, 2.5vw, 14px);
  color: #e0e0e0;
  transition: all 0.3s ease;
  border-radius: 20px;
  margin: 0 5px;
  text-transform: none;
}

#botoes:hover {
  background-color: rgba(142, 45, 226, 0.3);
  transform: translateY(-2px);
  box-shadow: 0 4px 15px rgba(142, 45, 226, 0.2);
  color: #ffffff;
}

@media (max-width: 768px) {
  .title {
    font-size: 16px;
  }
  
  #botoes {
    font-size: 12px;
    padding: 8px 12px;
    margin: 0 2px;
  }
}

@media (max-width: 480px) {
  .title {
    font-size: 14px;
  }
  
  #botoes {
    font-size: 10px;
    padding: 6px 8px;
    margin: 0 1px;
  }
}
</style>
