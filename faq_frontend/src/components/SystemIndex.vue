<template>
    <div class="system-index">
        <div class="title-content">
            <img src="../assets/tag_computer.png" alt="">
            <h1>PROGRAMAÇÃO</h1>
        </div>
        <div class="content-text-index">
            <span>TI - TECNOLOGIA DA INFORMAÇÃO</span>
            <h1>Saiba as principais dúvidas<br>da área da programação!</h1>
            <span>
                Você que está entrando na área da tecnologia e quer saber mais sobre<br> programação, tire suas dúvidas com as perguntas mais frequentes sobre<br> essa área em nosso site. 
            </span>
        </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'SystemIndex',
  }
  </script>
  
  <style scoped>
    .system-index {
      min-height: 100vh;
      min-width: 100vw;
      height: 100%;
      width: 100%;
    }
    .title-content{
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 30px;
        margin-top: 3rem;
    }
    .title-content h1{
        color: var(--branco);
        margin-left: 10px;
        font-size: 2vw;
    }
    .content-text-index {
        display: flex;
        flex-direction: column;
        /* justify-content: center; */
        align-items: center;
        padding: 8rem;
    }

    .content-text-index span{
        color: var(--roxo_claro);
        line-height: 1.5rem;
        text-align: center;
        font-size: 1vw;
    }

    .content-text-index h1{
        color: var(--branco);
        text-align: center;
        font-size: 3vw;

    }

  </style>
  