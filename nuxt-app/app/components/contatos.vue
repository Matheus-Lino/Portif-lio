<template>
  <div class="contatos-container">
    <div class="contatos-header">
      <h1 class="titulo-contatos">ENTRE EM CONTATO</h1>
      <p class="subtitulo-contatos">Vamos conversar sobre oportunidades e projetos</p>
    </div>
    
    <v-container>
      <v-row justify="center">
        <v-col cols="12" lg="8">
          <div class="contato-info">
            <h2 class="info-titulo">Informações de Contato</h2>
            <p class="info-descricao">
              Estou sempre aberto a novas oportunidades e colaborações. Entre em contato comigo através dos canais abaixo.
            </p>
            
            <div class="contato-items">
              <div class="contato-item" v-for="contato in contatos" :key="contato.id">
                <div class="contato-icone">
                  <v-icon :icon="contato.icone" size="24" color="#8e2de2"></v-icon>
                </div>
                <div class="contato-detalhes">
                  <h3 class="contato-titulo">{{ contato.titulo }}</h3>
                  <a 
                    v-if="contato.link" 
                    :href="contato.link" 
                    target="_blank" 
                    class="contato-valor link"
                  >
                    {{ contato.valor }}
                  </a>
                  <span v-else class="contato-valor">{{ contato.valor }}</span>
                  <p class="contato-descricao">{{ contato.descricao }}</p>
                </div>
              </div>
            </div>

            <div class="formulario-contato">
              <h2 class="info-titulo">Envie uma Mensagem</h2>
              <form @submit.prevent="enviarFormulario">
                <label>
                  Nome:
                  <input type="text" v-model="form.nome" required />
                </label>

                <label>
                  E-mail:
                  <input type="email" v-model="form.email" required />
                </label>

                <label>
                  Mensagem:
                  <textarea v-model="form.mensagem" required></textarea>
                </label>

                <button type="submit" :disabled="enviando">
                  {{ enviando ? "Enviando..." : "Enviar" }}
                </button>

                <transition name="fade">
                  <p v-if="feedback.message" :class="['feedback', feedback.type]">
                    {{ feedback.message }}
                  </p>
                </transition>
              </form>
            </div>

            <div class="redes-sociais">
              <h3 class="redes-titulo">Redes Sociais</h3>
              <div class="redes-buttons">
                <v-btn
                  v-for="rede in redesSociais"
                  :key="rede.nome"
                  :href="rede.link"
                  target="_blank"
                  :color="rede.cor"
                  variant="outlined"
                  class="rede-btn"
                  size="large"
                >
                  <v-icon :icon="rede.icone" class="mr-2"></v-icon>
                  {{ rede.nome }}
                </v-btn>
              </div>
            </div>
          </div>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'

const contatos = ref([
  {
    id: 1,
    titulo: 'E-mail',
    valor: 'matheuslinoeua@gmail.com',
    link: 'mailto:matheuslinoeua@gmail.com',
    icone: 'mdi-email',
    descricao: 'Respondo em até 24 horas'
  },
  {
    id: 2,
    titulo: 'Telefone',
    valor: '+55 (19) 99166-8445',
    link: 'tel:+5519991668445',
    icone: 'mdi-phone',
    descricao: 'WhatsApp disponível'
  }
])

const redesSociais = ref([
  {
    nome: 'LinkedIn',
    link: 'https://www.linkedin.com/in/matheus-lino-00ab92250/',
    icone: 'mdi-linkedin',
    cor: '#0077B5'
  },
  {
    nome: 'GitHub',
    link: 'https://github.com/Matheus-Lino',
    icone: 'mdi-github',
    cor: '#4338CA'
  },
  {
    nome: 'Instagram',
    link: 'https://instagram.com/theuslinoo',
    icone: 'mdi-instagram',
    cor: '#E4405F'
  }
])

const form = reactive({
  nome: '',
  email: '',
  mensagem: ''
})

const enviando = ref(false)

const feedback = reactive({
  message: '',
  type: '' // 'sucesso' ou 'erro'
})

const endpoint = 'https://formspree.io/f/xkgqvbyr'

async function enviarFormulario() {
  enviando.value = true
  feedback.message = ''
  feedback.type = ''

  const formData = new FormData()
  formData.append('name', form.nome)
  formData.append('email', form.email)
  formData.append('message', form.mensagem)

  try {
    const response = await fetch(endpoint, {
      method: 'POST',
      body: formData,
      headers: { Accept: 'application/json' }
    })

    if (response.ok) {
      feedback.message = 'Mensagem enviada com sucesso!'
      feedback.type = 'sucesso'
      form.nome = ''
      form.email = ''
      form.mensagem = ''
      // Faz a mensagem sumir após 4 segundos
      setTimeout(() => {
        feedback.message = ''
        feedback.type = ''
      }, 4000)
    } else {
      feedback.message = 'Erro ao enviar a mensagem. Tente novamente.'
      feedback.type = 'erro'
      setTimeout(() => {
        feedback.message = ''
        feedback.type = ''
      }, 4000)
    }
  } catch (error) {
    console.error(error)
    feedback.message = 'Erro ao enviar a mensagem. Tente novamente.'
    feedback.type = 'erro'
    setTimeout(() => {
      feedback.message = ''
      feedback.type = ''
    }, 4000)
  } finally {
    enviando.value = false
  }
}
</script>

<style scoped>

.contatos-container {
  min-height: 100vh;
  background: linear-gradient(135deg, rgba(0, 0, 0, 0.95), rgba(25, 20, 35, 0.9));
  padding: 60px 0;
  font-family: "Bitcount Single Ink", system-ui;
}

.contatos-header {
  text-align: center;
  margin-bottom: 60px;
  padding: 0 20px;
}
.titulo-contatos { font-family:"Bitcount Single Ink", system-ui; font-size:clamp(32px,6vw,48px); font-weight:700; background:linear-gradient(135deg,#8e2de2,#4a00e0); -webkit-background-clip:text; -webkit-text-fill-color:transparent; background-clip:text; margin-bottom:20px; letter-spacing:2px;}
.subtitulo-contatos {font-size:clamp(16px,3vw,20px); color:#b0a8c2; max-width:600px; margin:0 auto; line-height:1.6;}
.contato-info {padding:40px; background: rgba(25,20,35,0.85); backdrop-filter:blur(15px); -webkit-backdrop-filter:blur(15px); border:1px solid rgba(255,255,255,0.1); border-radius:20px; height:100%;}
.info-titulo {font-family:"Bitcount Single Ink",system-ui;font-size:28px;color:#f5f5f5;margin-bottom:20px;border-bottom:2px solid #8e2de2;padding-bottom:10px;}
.info-descricao {font-family:"Inter",system-ui,sans-serif;color:#c5c0d1;line-height:1.6;margin-bottom:40px;font-size:16px;}
.contato-items {margin-bottom:40px;}
.contato-item {display:flex; align-items:flex-start;margin-bottom:30px;padding:20px;background:rgba(255,255,255,0.05);border-radius:15px;border:1px solid rgba(255,255,255,0.1);transition:all 0.3s ease;}
.contato-item:hover {transform:translateY(-5px);box-shadow:0 10px 30px rgba(142,45,226,0.2);border-color:rgba(142,45,226,0.5);}
.contato-icone {margin-right:20px;padding:12px;background:rgba(142,45,226,0.2);border-radius:50%;border:1px solid rgba(142,45,226,0.3);}
.contato-detalhes {flex:1;}
.contato-titulo {font-family:"Bitcount Single Ink",system-ui;color:#e0e0e0;font-size:18px;margin-bottom:5px;}
.contato-valor {font-family:"Inter",system-ui,sans-serif;color:#c5c0d1;font-size:16px;margin-bottom:5px; display:block;}
.contato-valor.link {color:#8e2de2;text-decoration:none; transition:color 0.3s ease;}
.contato-valor.link:hover {color:#c39fff;text-decoration:underline;}
.contato-descricao {font-family:"Inter",system-ui,sans-serif;color:#9e9e9e;font-size:14px;margin:0;}

.formulario-contato {margin-top:40px; padding:30px; background: rgba(25,20,35,0.85); backdrop-filter:blur(15px); -webkit-backdrop-filter:blur(15px); border:1px solid rgba(142,45,226,0.3); border-radius:20px;}
.formulario-contato form label {display:block;margin-bottom:15px; font-family:"Inter",system-ui,sans-serif;color:#c5c0d1;}
.formulario-contato form input, .formulario-contato form textarea {width:100%; padding:10px; margin-top:5px; border-radius:10px; border:1px solid rgba(142,45,226,0.3); background:rgba(255,255,255,0.05); color:#fff; font-family:"Inter",system-ui,sans-serif; resize:vertical;}
.formulario-contato form textarea {min-height:120px;}
.formulario-contato form button {margin-top:15px;padding:12px 25px;background:linear-gradient(135deg,#8e2de2,#4a00e0);color:#fff;border:none;border-radius:25px;cursor:pointer;font-family:"Inter",system-ui,sans-serif;font-size:16px;transition:all 0.3s ease;}
.formulario-contato form button:hover {transform:translateY(-2px); box-shadow:0 8px 20px rgba(142,45,226,0.4);}
.formulario-contato form button:disabled {background: rgba(142,45,226,0.5); cursor:not-allowed;}

.feedback {margin-top:15px; font-family:"Inter",system-ui,sans-serif;font-size:15px; font-weight:500;}
.feedback.sucesso {color:#4caf50;}
.feedback.erro {color:#f44336;}

.fade-enter-active, .fade-leave-active {transition: opacity 0.5s;}
.fade-enter-from, .fade-leave-to {opacity:0;}

.redes-sociais {margin-top:40px;}
.redes-titulo {font-family:"Bitcount Single Ink",system-ui;color:#e0e0e0;font-size:20px;margin-bottom:20px;border-bottom:1px solid rgba(142,45,226,0.3);padding-bottom:10px;}
.redes-buttons {display:flex; flex-direction:column; gap:15px;}
.rede-btn {font-family:"Inter",system-ui,sans-serif !important;text-transform:none !important;border-radius:25px !important;transition:all 0.3s ease !important;justify-content:flex-start !important;}
.rede-btn:hover {transform:translateY(-2px); box-shadow:0 8px 20px rgba(142,45,226,0.4);}

@media (max-width:768px){.contatos-container{padding:40px 0;}.contatos-header{margin-bottom:40px;}.contato-info{padding:30px 20px;margin-bottom:30px;}.contato-item{flex-direction:column;text-align:center;}.contato-icone{margin:0 auto 15px;}.redes-buttons{flex-direction:row; flex-wrap:wrap; justify-content:center;}.rede-btn{flex:1; min-width:120px;}}
@media (max-width:480px){.info-titulo{font-size:24px;}.info-descricao{font-size:14px;}.contato-titulo{font-size:16px;}.contato-valor{font-size:14px;}.redes-buttons{flex-direction:column;}}
</style>
