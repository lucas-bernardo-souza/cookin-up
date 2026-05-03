<script lang="ts">
export default {
    data() {
        return {
            ingredientes: ['Alho', 'Manteiga', 'Orégano']
        }
    }
}
</script>

<template>
    <main class="conteudo-principal">
        <section>
            <span class="subtitulo-lg sua-lista-texto">
                Sua lista:
            </span>
            <!--
              A diretiva v-if é um condicional que se for avaliada como verdadeira o Vue irá renderizar o componente
              Caso a condição seja avaliada como falsa o Vue não renderizará o componente.
            -->

            <ul v-if="ingredientes.length" class="ingredientes-sua-lista">
              <!--
                Aqui está sendo realizado uma renderização dinâmica dos elementos dessa lista
                Para isso foi utilizado a diretiva v-for
                E é necessário um identificador único para cada componente
                Por meio da diretiva v-bind é possível usar a variavel js como atributo da tag key do html
                Com isso, foi passado o próprio valor da variável ingrediente como id único

                É possível omitir a diretiva v-bind e utilizar apenas os dois pontos :
              -->
                <li v-for="ingrediente in ingredientes" v-bind:key="ingrediente" class="ingrediente">
                    {{ ingrediente }}
                </li>
                
            </ul>
            <!--
              A diretiva v-else deve ser posicionada logo após um elemento que contenha e diretiva v-if
              E assim como na programação se um for renderizado o outro não será e visse versa
            -->
            <p v-else class="paragrafo lista-vazia">
              <img src="../assets/images/icones/lista-vazia.svg" alt="Ícone de pesquisa">
              Sua lista está vazia, selecione ingredientes para iniciar.
            </p>
        </section>
    </main>
</template>

<style scoped>
    .conteudo-principal {
  padding: 6.5rem 7.5rem;
  border-radius: 3.75rem 3.75rem 0rem 0rem;
  background: var(--creme, #FFFAF3);
  color: var(--cinza, #444);

  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 5rem;
}

.sua-lista-texto {
  color: var(--coral, #F0633C);
  display: block;
  text-align: center;
  margin-bottom: 1.5rem;
}

.ingredientes-sua-lista {
  display: flex;
  justify-content: center;
  gap: 1rem 1.5rem;
  flex-wrap: wrap;
}

.ingrediente {
  display: inline-block;
  border-radius: 0.5rem;
  min-width: 4.25rem;
  padding: 0.5rem;
  text-align: center;
    transition: 0.2s;
    color: var(--creme, #FFFAF3);
  background: var(--coral, #F0633C);
  font-weight: 700;
}

.lista-vazia {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  gap: 0.25rem;

  color: var(--coral, #F0633C);
  text-align: center;
}

@media only screen and (max-width: 1300px) {
  .conteudo-principal {
    padding: 5rem 3.75rem;
    gap: 3.5rem;
  }
}

@media only screen and (max-width: 767px) {
  .conteudo-principal {
    padding: 4rem 1.5rem;
    gap: 4rem;
  }
}

</style>