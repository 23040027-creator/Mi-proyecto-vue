<template>
  <div class="mi-componente">
    <h1 v-if="isVisible" :class="{ destacado: highlighted }">
      {{ message }}
    </h1>

    <button @click="toggleVisibility">
      Mostrar u ocultar mensaje
    </button>

    <button @click="toggleHighlight">
      Cambiar estilo
    </button>

    <input v-model="message" placeholder="Escribe un mensaje">

    <ul>
      <li v-for="item in list" :key="item.id">
        {{ item.text }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'MyComponent',

  data() {
    return {
      message: 'Hola mundo con Vue',
      isVisible: true,
      highlighted: false,
      list: [
        { id: 1, text: 'Primer elemento' },
        { id: 2, text: 'Segundo elemento' },
        { id: 3, text: 'Tercer elemento' }
      ]
    }
  },

  methods: {
    toggleVisibility() {
      this.isVisible = !this.isVisible
    },

    toggleHighlight() {
      this.highlighted = !this.highlighted
    }
  }
}
</script>

<style scoped>
.mi-componente {
  max-width: 480px;
  margin: 40px auto;
  padding: 32px;
  background-color: #ffffff;
  border-radius: 16px;
  box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.08), 0 8px 10px -6px rgba(0, 0, 0, 0.01);
  font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
  color: #1e293b;
  transition: all 0.3s ease;
}

h1 {
  font-size: 1.75rem;
  font-weight: 700;
  color: #334155;
  margin-top: 0;
  margin-bottom: 20px;
  min-height: 2.2rem; /* Evita que el contenedor salte al ocultar/mostrar */
  transition: color 0.3s ease, transform 0.2s ease;
}

/* Estado dinámico cuando highlighted es true */
.destacado {
  color: #2563eb;
  transform: scale(1.02);
  text-shadow: 0 2px 4px rgba(37, 99, 235, 0.15);
}

button {
  padding: 10px 18px;
  margin: 6px 8px 6px 0;
  border: none;
  border-radius: 8px;
  background-color: #ff55e8;
  color: #ffffff;
  font-weight: 600;
  font-size: 0.9rem;
  cursor: pointer;
  transition: background-color 0.2s ease, transform 0.1s ease, box-shadow 0.2s ease;
}

button:hover {
  background-color: #f3f02e;
  box-shadow: 0 4px 12px rgba(241, 21, 32, 0.25);
}

button:active {
  transform: scale(0.97);
}

input {
  display: block;
  width: 100%;
  box-sizing: border-box;
  margin-top: 20px;
  margin-bottom: 24px;
  padding: 12px 16px;
  border: 2px solid #e2e8f0;
  border-radius: 8px;
  font-size: 0.95rem;
  color: #1e293b;
  outline: none;
  transition: border-color 0.2s ease, box-shadow 0.2s ease;
}

input:focus {
  border-color: #90adec;
  box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.15);
}

input::placeholder {
  color: #94a3b8;
}

ul {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

li {
  padding: 12px 16px;
  background-color: #f8fafc;
  border: 1px solid #f1f5f9;
  border-radius: 8px;
  color: #475569;
  font-size: 0.95rem;
  transition: background-color 0.2s ease, transform 0.2s ease;
}

li:hover {
  background-color: #f1f5f9;
  transform: translateX(4px);
}
</style>