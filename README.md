# La API de composición 

Es una forma de crear componentes en Vue.js que no se basa en la opción data. En su lugar, utiliza funciones para crear componentes, lo que le da un mayor control sobre la forma en que se crean y se conectan los componentes.

Una de las ventajas de usar la API de composición es que puede crear componentes más modulares. Esto significa que puede dividir sus componentes en partes más pequeñas y reutilizables. Esto puede hacer que sus componentes sean más fáciles de entender y mantener.

Otra ventaja de usar la API de composición es que puede crear componentes más personalizados. Esto se debe a que puede usar las funciones proporcionadas por la API de composición para crear componentes que se adapten mejor a sus necesidades específicas.


# Qué es el State en Vue.js

El state (o estado) determina la situación actual de nuestra aplicacion. El state o estado no es siempre igual: tiende a cambiar en base a las interacciones de uusario (clicks, formularios, etc)

# Reactive y ref

reactive y ref son funciones que se usan para crear objetos y referencias reactivas, respectivamente. Los objetos y referencias reactivas son una forma de almacenar datos que pueden ser observados por Vue para cambios. Cuando se cambia un objeto o referencia reactiva, Vue actualiza automáticamente los componentes que dependen de él. Esto hace que sea fácil mantener los componentes de Vue sincronizados con los datos subyacentes.

## Reactive

reactive es una función que crea un objeto reactivo. Un objeto reactivo es un objeto que puede ser observado por Vue para cambios. Cuando se cambia un objeto reactivo, Vue actualiza automáticamente los componentes que dependen de él. Esto hace que sea fácil mantener los componentes de Vue sincronizados con los datos subyacentes.

Aquí hay un ejemplo de cómo usar reactive:

````
const state = reactive({
  count: 0
});

//Incrementa el contador
state.count++;

//Muestra el valor del contador en la interfaz de usuario
<p>{{ state.count }}</p>
````

En este ejemplo, usamos la función reactive para crear un objeto reactivo llamado state. El objeto state tiene una propiedad llamada count que es un número. Cuando incrementamos el valor de count, Vue actualiza automáticamente la interfaz de usuario para mostrar el nuevo valor.

## Ref

ref es una función que crea una referencia reactiva. Una referencia reactiva es una referencia a un valor que puede ser observado por Vue para cambios. Cuando se cambia el valor al que se hace referencia, Vue actualiza automáticamente los componentes que dependen de él. Esto hace que sea fácil mantener los componentes de Vue sincronizados con los datos subyacentes.

Aquí hay un ejemplo de cómo usar ref:

````
//El 0 entre paréntesis es el valor inicial del contador. Cuando creas una referencia reactiva con la función ref, puedes proporcionarle un valor inicial. En este caso, el valor inicial es 0. 
//Esto significa que cuando el componente se cargue, el contador se establecerá en 0. Cuando incrementes el contador, su valor aumentará en 1. El nuevo valor se reflejará en la interfaz de usuario.

const counter = ref(0);

//Incrementa el contador
counter.value++;

//Muestra el valor del contador en la interfaz de usuario
<p>{{ counter.value }}</p>
````

En este ejemplo, usamos la función ref para crear una referencia reactiva llamada counter. La referencia counter apunta a un número. Cuando incrementamos el valor de counter, Vue actualiza automáticamente la interfaz de usuario para mostrar el nuevo valor.

## Diferencias entre reactive y ref

La diferencia principal entre reactive y ref es que reactive crea un objeto reactivo, mientras que ref crea una referencia reactiva. Un objeto reactivo es un objeto que puede ser observado por Vue para cambios, mientras que una referencia reactiva es una referencia a un valor que puede ser observado por Vue para cambios.

En general, deberías usar reactive cuando necesites un objeto reactivo, mientras que deberías usar ref cuando necesites una referencia reactiva. Por ejemplo, si necesitas crear un objeto que contenga datos que se actualizarán automáticamente, deberías usar reactive. Si necesitas crear una referencia a un valor que se actualizará automáticamente, deberías usar ref.

#### Aquí hay algunos ejemplos de cuándo deberías usar reactive:

- Cuando necesitas crear un objeto que contenga datos que se actualizarán automáticamente.
- Cuando necesitas crear un objeto que se pueda usar en una plantilla de Vue.
- Cuando necesitas crear un objeto que se pueda usar con la API de composición de Vue.

#### Aquí hay algunos ejemplos de cuándo deberías usar ref:

- Cuando necesitas crear una referencia a un valor que se actualizará automáticamente.
- Cuando necesitas crear una referencia a un valor que se pueda usar en una función.
- Cuando necesitas crear una referencia a un valor que se pueda usar con la API de composición de Vue.

# Una directiva en Vue 

Es una función que se puede usar para agregar funcionalidad a un elemento HTML. Las directivas se pueden usar para agregar comportamiento a un elemento, para cambiar su presentación o para ambas cosas.

Las directivas en Vue se escriben usando el atributo v- seguido del nombre de la directiva. Por ejemplo, la directiva v-on se usa para agregar eventos a un elemento, y la directiva v-bind se usa para enlazar datos a un elemento.

Aquí hay algunos ejemplos de directivas en Vue:

v-on: Esta directiva se usa para agregar eventos a un elemento. Por ejemplo, el siguiente código agrega un evento click al elemento <button>:

````
<button v-on:click="doSomething()">Click me</button>
````

v-bind: Esta directiva se usa para enlazar datos a un elemento. Por ejemplo, el siguiente código enlazar el valor de la variable message al elemento <p>:

````
<p v-bind:text="message"></p>
````

v-if: Esta directiva se usa para mostrar o ocultar un elemento según una condición. Por ejemplo, el siguiente código mostrará el elemento <div> solo si la variable isVisible es true:

````
<div v-if="isVisible">This text will be displayed only if isVisible is true.</div>
````

v-for: Esta directiva se usa para iterar sobre una colección de datos y generar elementos HTML. Por ejemplo, el siguiente código genera una lista de elementos <li> para cada elemento en la colección items:

````
<ul v-for="item in items">
  <li>{{ item }}</li>
</ul>
````

Las directivas en Vue son una poderosa herramienta que puede usarse para agregar funcionalidad a los componentes de Vue.

# Los props 

son propiedades que se pueden pasar a un componente de Vue desde su entorno. Se pueden usar para pasar datos al componente o para configurar su comportamiento.

Los props se definen usando el atributo prop en la definición del componente. El atributo prop debe tener un nombre y un tipo. El tipo puede ser cualquier tipo de datos válido en JavaScript, como string, number, object o array.

````
<script setup>
const props = defineProps({
    guitarra:{
        type: Object,
        required: true
    }
})
</script>
````

````
<Guitarra 
    v-for="guitarra in guitarras"
    v-bind:guitarra="guitarra"
    />
````

# Computed Property (Propiedad Computada):

Una propiedad computada es una propiedad en un componente Vue que se deriva de una o más propiedades existentes, realizando algún cálculo o procesamiento en el proceso. Las propiedades computadas se almacenan en caché y solo se recalculan cuando las dependencias cambian. Son útiles para realizar operaciones más complejas y para mantener el código limpio y organizado. Las propiedades computadas se declaran utilizando la función computed.

En resumen es una función que se ejecuta cuando una o más de sus dependencias cambian. Las propiedades computadas se definen usando la sintaxis computed. Por ejemplo, la siguiente propiedad computada calcula el área de un cuadrado:

````
import { computed } from 'vue'

computed: {
  area() {
    return this.length  * this.width;
  }
}
````

La propiedad computada area se ejecutará cada vez que los valores de length o width cambien. Las propiedades computadas se pueden usar para calcular valores, formatear texto o realizar otras operaciones que dependen de los valores de otras propiedades.

Las propiedades computadas son una herramienta poderosa que puede ayudarte a escribir código más claro y conciso. También pueden ayudarte a mejorar el rendimiento de tu aplicación al evitar que se ejecuten funciones innecesarias.

# Props (Propiedades):

Las propiedades son valores que se pasan de un componente padre a un componente hijo en Vue. Permiten la comunicación entre componentes y se utilizan para enviar datos desde el componente padre al componente hijo. Las propiedades se declaran en el componente hijo utilizando la función defineProps en el nuevo <script setup>. Estas propiedades pueden ser utilizadas como si fueran variables locales dentro del componente hijo.

````
App.vue

<script setup>
  const guitarra = ref({});

  onMounted(() => {
    guitarra.value = db[3];
  });
</script>

<template>
  <Header 
    :guitarra="guitarra" 
  />
</template>
````

````
Header.vue

<script setup>
  const props = defineProps({      
          guitarra: {
              type: Object,
              required: true
          }
      })
</script>

<template>
    <div  class="row mt-5">
                <div class="col-md-6 text-center text-md-start pt-5">
                    <h1 class="display-2 fw-bold">Modelo {{guitarra.nombre}}</h1>                  
                </div>
    </div>
</template>
````

# DefineEmits 

es una función que se usa para definir los eventos que un componente puede emitir. Los eventos se definen como una matriz de objetos, donde cada objeto tiene dos propiedades: name y args. La propiedad name es el nombre del evento, y la propiedad args es un arreglo de argumentos que se pasarán al evento cuando se emita.

````
App.vue

<script setup>
  const decrementarCantidad = (id) => {
    const index = carrito.value.findIndex((producto) => producto.id === id);
    if (carrito.value[index].cantidad <= 1) return;
    carrito.value[index].cantidad--;
  };
</script>

<template>
<Header  
    @decrementar-cantidad="decrementarCantidad"   
  />
</template>
````

Por ejemplo, el siguiente código define un componente que puede emitir un eventos:

````
Header.vue

<script setup>
 defineEmits(['decrementar-cantidad'])
</script>

````

Para emitir un evento, se usa la función $emit. La función $emit toma dos argumentos: el nombre del evento y los argumentos que se pasarán al evento. Por ejemplo, el siguiente código emite el evento onSubmit con los argumentos.

````
Header.vue

<template>
 <button
      type="button"
      class="btn btn-dark"
      @click="$emit('decrementar-cantidad', producto.id)"
  >
      -
  </button>
</template>
````