
<template>

    <div class="alert alert-dark" role="alert">
    Um simples alerta dark. Olha só!
    </div>

    <button type="button" class="btn btn-primary">Botão Bootstrap</button>

    <div class="alert alert-success" role="alert">
    <h4 class="alert-heading">Muito bem!</h4>
    <p>Aêêê! Você conseguiu ler essa mensagem de alerta. Esse texto vai ter quer se extender um pouquinho pra você conseguir ver como o espaçamento dentro de um alerta funciona.</p>
    <hr>
    <p class="mb-0">Sempre que precisar, use utilitários de margem para manter as coisas perfeitas.</p>
    </div>

</template>

<script>

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}

</script>
