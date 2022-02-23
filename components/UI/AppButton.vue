<template>
  <button
    class="btn btn-blue btn-blue:hover mx-2 mb-2"
    :class="btnStyle"
    v-bind="$attrs" 
    v-on="$listeners"><slot /></button>
    <!--v-bin: Agregar caracteristicas a la etiqueta-->
    <!--v-on: Agregar eventos a la etiqueta-->
</template>

<script>
export default {
  name: 'AppButton',
  props: {
    btnStyle: {
      type: String,
      default: ''
    }
  }
}
</script>

