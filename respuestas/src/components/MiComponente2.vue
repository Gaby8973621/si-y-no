<!-- PARTE DEL COMPONENTE 1 
  <template>
  <h1>Primer componente</h1>

  <h1 class="text-3xl font-bold underline">Hello world!</h1>
  <section>
    <h3>numero - {{ numero }}</h3>
    <h3>Multiplicacion {{ contador }}</h3>
  </section>

  <button @click="numero++">+1</button>
  <button @click="numero--">-1</button>
</template>

<script lang="ts" setup>
import { computed, ref } from 'vue'

//DEFINE EL PROPS
interface Props {
  value: number
}
const props = defineProps<Props>()

const numero = ref(props.value)
//FINALISA EL PROPS

const contador = computed(() => numero.value * numero.value)
</script>
<style scoped>
h3 {
  color: red;
}
</style>

-->

<!-- PARTE DEL COMPONENTE 2 
<template>
  <h1>Primer componente</h1>

  <h3>{{ numero }}</h3>
  <button @click="incrementar">+1</button>
  <button @click="decrementar">-1</button>
</template>

<script lang="ts">
import { computed, ref, defineComponent } from 'vue'

export default defineComponent({
  props: {
    value: { type: Number, required: true } // Definimos el prop 'value'
  },
  setup(props) {
    const numero = ref(props.value) // Usamos el valor del prop como estado local
    const contador = computed(() => numero.value * numero.value) // Computamos el valor al cuadrado de 'numero'

    // Funciones para incrementar y decrementar el valor de 'numero'
    const incrementar = () => {
      numero.value++
    }

    const decrementar = () => {
      numero.value--
    }

    return {
      numero,
      contador,
      incrementar,
      decrementar
    }
  }
})
</script>

<style scoped>
h3 {
  color: red;
}
</style> 



<style scoped>
.chat-container {
  background-color: #fff;
  width: 400px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  border-radius: 10px;
  overflow: hidden;
}

#chat-container {
  display: flex;
  flex-direction: column;
  height: 500px;
}

.chat-header {
  background-color: #2c3e50;
  color: white;
  padding: 1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.chat-title {
  font-size: 1.25rem;
  font-weight: 600;
}

.close-btn {
  background: none;
  border: none;
  color: white;
  cursor: pointer;
}

.icon {
  width: 20px;
  height: 20px;
}

.chatbox {
  padding: 1rem;
  flex: 1;
  overflow-y: auto;
  background-color: #f7f8fa;
}

.message {
  display: flex;
  margin-bottom: 1rem;
}

.right {
  justify-content: flex-end;
}

.left {
  justify-content: flex-start;
}

.bubble {
  padding: 0.75rem 1rem;
  border-radius: 20px;
  max-width: 75%;
  font-size: 0.9rem;
  line-height: 1.4;
}

.right-bubble {
  background-color: #007bff;
  color: white;
  margin-left: auto;
}

.left-bubble {
  background-color: #e9ecef;
  color: #333;
}

.input-area {
  padding: 0.5rem;
  background-color: #f0f2f5;
  border-top: 1px solid #ddd;
  display: flex;
  gap: 0.5rem;
}

.input-field {
  flex: 1;
  padding: 0.75rem;
  border: 1px solid #ccc;
  border-radius: 5px;
  font-size: 0.9rem;
}

.send-btn {
  background-color: #007bff;
  color: white;
  padding: 0.75rem 1rem;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.send-btn:hover {
  background-color: #0056b3;
}

.response-image {
  display: none;
  max-width: 100px;
  margin-top: 0.5rem;
  border-radius: 10px;
}
</style>-->
