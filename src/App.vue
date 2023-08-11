<script setup>
import { ref, reactive, onMounted, watch } from "vue";
import { db } from "./data/guitarras";
import Guitarra from "./components/Guitarra.vue";
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";

// Crea una instancia de la clase Guitarra y la asigna a la variable guitarra.
const guitarras = ref([]);

// Crea una instancia de la clase Carrito y la asigna a la variable carrito.
const carrito = ref([]);

// Crea una instancia de la clase Guitarra y la asigna a la variable guitarra.
const guitarra = ref({});

// Observa los cambios en la variable carrito y ejecuta la función guardarLocalStorage cuando se produzcan cambios.
watch(
  carrito,
  () => {
    guardarLocalStorage();
  },
  {
    // Entra a todos los atributos del carrito para escuchar/ver si hay cambios
    deep: true,
  }
);

// Se ejecuta cuando el componente se monta en el DOM.
onMounted(() => {
  // Asigna el contenido del archivo data/guitarras.json a la variable guitarras.
  guitarras.value = db;

  // Asigna el contenido del tercer elemento del archivo data/guitarras.json a la variable guitarra.
  guitarra.value = db[3];

  // Comprueba si existe un elemento en el almacenamiento local con la clave carrito.
  const carritoStorage = localStorage.getItem("carrito");

  // Si existe, descodifica el elemento del almacenamiento local y lo asigna a la variable carrito.
  if (carritoStorage) {
    carrito.value = JSON.parse(carritoStorage);
  }
});

// Guarda el carrito en el almacenamiento local.
const guardarLocalStorage = () => {
  // Codifica el carrito y lo guarda en el almacenamiento local con la clave carrito.
  localStorage.setItem("carrito", JSON.stringify(carrito.value));
};

// Añade una guitarra al carrito.
const agregarCarrito = (guitarra) => {
  // Busca la guitarra en el carrito.
  const existeCarrito = carrito.value.findIndex(
    (producto) => producto.id === guitarra.id
  );

  // Si la guitarra ya existe en el carrito, incrementa la cantidad.
  if (existeCarrito >= 0) {
    if (carrito.value[existeCarrito].cantidad >= 5) return;
    carrito.value[existeCarrito].cantidad++;
  } else {
    // Si la guitarra no existe en el carrito, la añade con una cantidad de 1.
    guitarra.cantidad = 1;
    carrito.value.push(guitarra);
  }
};

// Decrementa la cantidad de una guitarra en el carrito.
const decrementarCantidad = (id) => {
  // Busca la guitarra en el carrito.
  const index = carrito.value.findIndex((producto) => producto.id === id);

  // Si la cantidad es 1, elimina la guitarra del carrito.
  if (carrito.value[index].cantidad <= 1) return;
  carrito.value[index].cantidad--;
};

// Incrementa la cantidad de una guitarra en el carrito.
const incrementarCantidad = (id) => {
  // Busca la guitarra en el carrito.
  const index = carrito.value.findIndex((producto) => producto.id === id);

  // Si la cantidad es 5, no hace nada.
  if (carrito.value[index].cantidad >= 5) return;
  carrito.value[index].cantidad++;
};

// Elimina una guitarra del carrito.
const eliminarProducto = (id) => {
  // Elimina la guitarra del carrito.
  carrito.value = carrito.value.filter((producto) => producto.id !== id);
};

// Vacía el carrito.
const vaciarCarrito = () => {
  // Vacía el carrito.
  carrito.value = [];
};
</script>

<template>
  <Header
    :carrito="carrito"
    :guitarra="guitarra"
    @decrementar-cantidad="decrementarCantidad"
    @incrementar-cantidad="incrementarCantidad"
    @agregar-carrito="agregarCarrito"
    @eliminar-producto="eliminarProducto"
    @vaciar-carrito="vaciarCarrito"
  />

  <main class="container-xl mt-5">
    <h2 class="text-center">Nuestra Colección</h2>

    <div class="row mt-5">
      <Guitarra
        v-for="guitarra in guitarras"
        :key="guitarra.id"
        :guitarra="guitarra"
        @agregar-carrito="agregarCarrito"
      />
    </div>
  </main>

  <Footer />
</template>
