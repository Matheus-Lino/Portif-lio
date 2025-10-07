<template>
    <v-app>
      <navbar/>
      <sobre/>
      <div id="projetos">
        <projetos/>
      </div>
      <div id="contatos">
        <contatos/>
      </div>
    </v-app>
</template>

<script setup>
import SvgIcon from '@jamescoyle/vue-icon'
import { mdiAccount } from '@mdi/js'
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Bitcount+Single+Ink:wght@100..900&family=SUSE+Mono:ital,wght@0,100..800;1,100..800&family=Slabo+13px&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Bitcount+Single+Ink:wght@100..900&family=Slabo+13px&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');

* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  scroll-behavior: smooth;
}

html {
  scroll-behavior: smooth;
}

.v-application__wrap {
  background-color: rgba(0, 0, 0, 0.966);
}

#sobre {
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.95), rgba(240, 240, 255, 0.9));
  min-height: 100vh;
  display: flex;
  align-items: center;
}

#projetos {
  background: linear-gradient(135deg, rgba(0, 0, 0, 0.95), rgba(25, 20, 35, 0.9));
  min-height: 100vh;
}

#contatos {
  background: linear-gradient(135deg, rgba(0, 0, 0, 0.95), rgba(25, 20, 35, 0.9));
  min-height: 100vh;
}

@media (max-width: 768px) {
  #sobre,
  #projetos,
  #contatos {
    min-height: auto;
    padding: 20px 0;
  }
}
</style>
