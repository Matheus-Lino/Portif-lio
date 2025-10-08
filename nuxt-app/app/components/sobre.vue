<template>

    <div class="pa-4 text-center">
        <v-avatar class="avatar" :image="imagem" size="200"></v-avatar>
        <h1 id="animacao-titulo"></h1>
        <p class="sobre" id="animacao-texto"></p>
        <v-dialog max-width="900">
            <template v-slot:activator="{ props: activatorProps }">
                <v-btn id="botao-sobremim" v-bind="activatorProps" text="Sobre mim"></v-btn>
                <a href="../assets/Curriculo-Matheus-Atualizado.pdf" download style="margin-left: 15px; text-decoration: none;">
                    <v-btn id="botao-sobremim" text="Download CV"></v-btn>
                </a>
            </template>

            <template v-slot:default="{ isActive }">
                <v-card class="sobre-mim-dark" title="SOBRE MIM">
                    <template v-slot:text>
                        <div class="sobre-mim-conteudo">
                            <div class="header-perfil">
                                <v-avatar :image="imagem" size="100" class="perfil-avatar-interno"></v-avatar>
                                <h2 class="titulo">Matheus Lino</h2>
                                <p class="introducao">
                                    <strong>Desenvolvedor Full Stack</strong> formado em Análise e Desenvolvimento de
                                    Sistemas, possuo experiência na criação de aplicações web completas, abrangendo
                                    desde o front-end até o back-end.
                                </p>
                            </div>

                            <div class="secao">
                                <h3 class="subtitulo">💼 Experiência Profissional</h3>
                                <ul class="lista-custom">
                                    <li><strong>Desenvolvedor Front-end na GRV Software</strong> (Maio/2024 -
                                        Abril/2025).
                                        Atuei no desenvolvimento front-end de um sistema ERP <strong>IoT</strong>, uma
                                        plataforma para integração de dispositivos inteligentes e monitoramento de dados
                                        em tempo real, utilizando Vue.js, Nuxt e TypeScript.</li>
                                    <li>Responsável por desenvolver componentes reutilizáveis e escaláveis, implementar
                                        recursos interativos para otimizar a experiência do usuário e realizar
                                        integrações com APIs e back-end.</li>
                                    <li>Trabalho em equipe, focando em usabilidade, performance e entregas ágeis, além
                                        de desenvolver consultas em <strong>SQL Server</strong> e lógica de programação
                                        para soluções full stack.</li>
                                    <li>Experiência com versionamento de código (Git/GitHub) e metodologia ágil
                                        (Kanban).</li>
                                </ul>
                            </div>

                            <div class="secao">
                                <h3 class="subtitulo">🎓 Educação</h3>
                                <ul class="lista-custom">
                                    <li><strong>Tecnólogo em Análise e Desenvolvimento de Sistemas</strong> -
                                        Universidade Paulista (UNIP) (2023 - 2025).</li>
                                    <li><strong>Ensino Médio Completo</strong> - E.E Professor João Lourenço Rodrigues
                                        (2018 - 2020).</li>
                                </ul>
                            </div>

                            <div class="secao">
                                <h3 class="subtitulo">🚀 Habilidades Técnicas (Hard Skills)</h3>
                                <ul class="lista-custom">
                                    <li><strong>Front-end:</strong> HTML5, CSS3, JavaScript (ES6+), Vue.js, Nuxt.js,
                                        TypeScript (básico).</li>
                                    <li><strong>Back-end:</strong> Node.js, Python.</li>
                                    <li><strong>Banco de Dados:</strong> SQL Server.</li>
                                    <li><strong>Ferramentas e Práticas:</strong> Git, GitHub, VS Code, Figma, UX/UI
                                        Design, Web Performance, Acessibilidade.</li>
                                </ul>
                            </div>

                            <div class="secao">
                                <h3 class="subtitulo">💡 Habilidades Comportamentais (Soft Skills)</h3>
                                <ul class="lista-custom">
                                    <li>Trabalho em equipe, Comunicação clara e objetiva, Resiliência e adaptabilidade a
                                        mudanças, Organização e atenção aos detalhes, Aprendizado Contínuo e
                                        Proatividade.</li>
                                </ul>
                            </div>

                            <div class="secao">
                                <h3 class="subtitulo">🏆 Certificações</h3>
                                <ul class="lista-custom">
                                    <li><strong>Rocketseat:</strong> NLW Unite - Csharp, NLW Unite - Reactjs, NLW Expert
                                        trilha de HTML, CSS e Javascript, Discover, Conectar.</li>
                                    <li><strong>Nube:</strong> Mercado de Trabalho e Processo Seletivo: como
                                        enfrentá-los?.</li>
                                </ul>
                            </div>

                            <div class="secao objetivo-secao">
                                <h3 class="subtitulo">🎯 Objetivo</h3>
                                <p class="objetivo-texto">
                                    Busco integrar-me a uma equipe como Desenvolvedor Front-end, aplicando minhas
                                    experiências em HTML, CSS, JavaScript e, especialmente, no desenvolvimento de
                                    interfaces dinâmicas com Vue.js. Meu foco é entregar soluções de alta qualidade que
                                    aprimorem a experiência do usuário e a performance da aplicação.
                                </p>
                            </div>
                        </div>
                    </template>

                    <v-card-actions class="card-actions">
                        <v-spacer></v-spacer>
                        <v-btn id="botao-fechar" text="Fechar" @click="isActive.value = false"></v-btn>
                    </v-card-actions>
                </v-card>
            </template>
        </v-dialog>
    </div>
</template>

<script setup>
import imagem from "../assets/WhatsApp Image 2025-09-24 at 17.18.33 (2).jpg"
import TypeIt from "typeit";
import { onMounted } from "vue";

onMounted(() => {
    new TypeIt("#animacao-texto", {
        speed: 60,
        waitUntilVisible: true,
        loop: true,
    })
        .type("Desenvolvedor Full Stack!")
        .pause(1000)
        .delete()
        .type("Apaixonado por Técnologia!")
        .pause(1000)
        .delete()
        .type("Sempre disposto e aprendendo coisas novas!")
        .pause(1000)
        .delete()
        .type("Criativo e focado em resultados!")
        .pause(1000)
        .delete()
        .type("Trabalho em equipe!")
        .pause(1000)
        .delete()
        .type("Organizado e comunicativo!")
        .pause(1000)
        .delete()
        .go();


    new TypeIt("#animacao-titulo", {
        speed: 90,
        waitUntilVisible: true,
        loop: false,
    })
        .type("Olá, me chamo Matheus👋🏻")
        .go();
});
</script>

<style scoped>
.avatar {
    height: 100%;
    margin-top: 10%;
    align-self: center;
    border: 4px solid rgba(63, 0, 71, 0.2);
    box-shadow: 0 8px 32px rgba(63, 0, 71, 0.15);
    transition: all 0.3s ease;
}

.avatar:hover {
    transform: scale(1.05);
    box-shadow: 0 12px 40px rgba(63, 0, 71, 0.25);
}

h1 {
    font-family: "Bitcount Single Ink", system-ui;
    font-size: clamp(28px, 5vw, 40px);
    text-align: center;
    margin-top: 15px;
    background: linear-gradient(135deg, #3c0063, #6a1b9a);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
}

.sobre {
    font-family: "Bitcount Single Ink", system-ui;
    text-align: center;
    font-size: clamp(16px, 3vw, 20px);
    color: #555;
    margin-bottom: 20px;
}

#botao-sobremim {
    background: linear-gradient(135deg, rgba(63, 0, 71, 0.4), rgba(106, 27, 154, 0.4));
    border-radius: 25px;
    font-family: "Bitcount Single Ink", system-ui;
    font-size: 20px;
    color: white;
    padding: 12px 24px;
    box-shadow: 0 4px 15px rgba(63, 0, 71, 0.3);
    transition: all 0.3s ease;
    text-transform: none;
    font-weight: 500;
}

#botao-sobremim:hover {
    background: linear-gradient(135deg, rgba(63, 0, 71, 0.6), rgba(106, 27, 154, 0.6));
    transform: translateY(-2px);
    box-shadow: 0 6px 20px rgba(63, 0, 71, 0.4);
}

.sobre-mim-dark {
    background: rgba(25, 20, 35, 0.85);
    font-family: "Bitcount Single Ink", system-ui;
    backdrop-filter: blur(15px);
    -webkit-backdrop-filter: blur(15px);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 20px;
    box-shadow: 0 20px 60px rgba(0, 0, 0, 0.4);
    color: #e0e0e0;
}

.sobre-mim-dark .v-card-title {
    background: linear-gradient(135deg, #8e2de2, #4a00e0);
    color: white;
    font-family: "Bitcount Single Ink", system-ui;
    font-size: 24px;
    font-weight: 600;
    text-align: center;
    padding: 20px;
    letter-spacing: 1.5px;
    border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.sobre-mim-conteudo {
    font-family: "Inter", system-ui, sans-serif;
    line-height: 1.8;
    padding: 20px 30px 30px;
}

.header-perfil {
    text-align: center;
    margin-bottom: 35px;
    animation: fadeInDown 0.8s ease-out;
}

.perfil-avatar-interno {
    border: 3px solid #8e2de2;
    box-shadow: 0 0 25px rgba(142, 45, 226, 0.5);
    margin-bottom: 15px;
}

.titulo {
    font-family: "Bitcount Single Ink", system-ui;
    font-size: clamp(24px, 4vw, 32px);
    font-weight: 700;
    color: #f5f5f5;
    margin-bottom: 10px;
}

.introducao {
    font-size: 16px;
    max-width: 600px;
    margin: 0 auto;
    color: #b0a8c2;
}

.secao {
    margin-bottom: 30px;
    padding: 25px;
    background: rgba(255, 255, 255, 0.05);
    border-radius: 15px;
    border: 1px solid rgba(255, 255, 255, 0.1);
    transition: all 0.3s ease;
    animation: fadeInUp 0.6s ease-out forwards;
    opacity: 0;
}

.secao:nth-of-type(1) {
    animation-delay: 0.2s;
}

.secao:nth-of-type(2) {
    animation-delay: 0.4s;
}

.secao:nth-of-type(3) {
    animation-delay: 0.6s;
}


.secao:hover {
    transform: translateY(-5px) scale(1.02);
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
    border-color: rgba(142, 45, 226, 0.5);
}

.subtitulo {
    font-size: 22px;
    font-weight: 600;
    margin-bottom: 20px;
    color: #e0e0e0;
    font-family: "Bitcount Single Ink", system-ui;
    display: flex;
    align-items: center;
    gap: 12px;
    border-bottom: 2px solid #8e2de2;
    padding-bottom: 10px;
}

.lista-custom {
    list-style: none;
    padding-left: 0;
}

.lista-custom li {
    margin-bottom: 15px;
    padding-left: 25px;
    position: relative;
    font-size: 16px;
    color: #c5c0d1;
}

.lista-custom li::before {
    content: '⚡';
    position: absolute;
    left: 0;
    top: 2px;
    color: #8e2de2;
    font-size: 16px;
    transition: transform 0.3s ease;
}

.lista-custom li:hover::before {
    transform: scale(1.3);
}

.objetivo-secao {
    background: linear-gradient(135deg, rgba(142, 45, 226, 0.1), rgba(74, 0, 224, 0.15));
    border: 1px solid rgba(142, 45, 226, 0.4);
}

.objetivo-texto {
    font-size: 17px;
    font-style: italic;
    text-align: center;
    color: #f0eaff;
    margin: 0;
}

strong {
    color: #a16eff;
    font-weight: 600;
    transition: color 0.3s ease;
}

strong:hover {
    color: #c39fff;
}

.card-actions {
    background: rgba(25, 20, 35, 0.9);
    padding: 15px 30px;
    border-top: 1px solid rgba(255, 255, 255, 0.1);
}

#botao-fechar {
    background: transparent;
    border: 2px solid #8e2de2;
    color: #e0e0e0;
    border-radius: 25px;
    padding: 8px 20px;
    font-family: "Inter", system-ui, sans-serif;
    font-weight: 500;
    transition: all 0.3s ease;
    text-transform: none;
}

#botao-fechar:hover {
    background: #8e2de2;
    color: white;
    box-shadow: 0 0 20px rgba(142, 45, 226, 0.6);
    transform: translateY(-2px);
}

@keyframes fadeInUp {
    from {
        opacity: 0;
        transform: translateY(30px);
    }

    to {
        opacity: 1;
        transform: translateY(0);
    }
}

@keyframes fadeInDown {
    from {
        opacity: 0;
        transform: translateY(-20px);
    }

    to {
        opacity: 1;
        transform: translateY(0);
    }
}

@media (max-width: 768px) {
    .sobre-mim-conteudo {
        padding: 20px;
    }

    .subtitulo {
        font-size: 20px;
    }

    .lista-custom li,
    .introducao,
    .objetivo-texto {
        font-size: 15px;
    }
}
</style>