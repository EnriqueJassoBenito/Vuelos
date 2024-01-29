<template>
  <div>
    <h1 class="text-center">Hola esto es un formulario</h1>

    <b-form @submit.stop.prevent="onSubmit">

      <b-container class="">
        <b-row >
          <b-col cols="6">
            <h3>Datos</h3>
            <!-- Nombre completo -->
            <b-form-group id="name-1" label="Nombre" label-for="name" description="">
              <b-form-input 
                id="name" 
                name="name"
                placeholder="Ingresa el nombre" 
                v-model="form.name" 
                v-validate="{ required: true, min: 3, max: 20, alpha }"
                :state="validateState('name')" 
                aria-describedby="name-feedback"
                data-vv-as="Nombre">
              </b-form-input>
              <b-form-invalid-feedback id="name-feedback">Debe ingresar el nombre</b-form-invalid-feedback>
            </b-form-group>

            <b-form-group id="lastname-1" label="Apellido Paterno" label-for="lastname">
              <b-form-input 
                id="lastname"
                name="lastname" 
                placeholder="Ingresa apellido paterno" 
                v-model="form.lastname" 
                v-validate="{ required: true, min: 4, max: 10, alpha }" 
                :state="validateState('lastname')"
                aria-describedby="lastname-feedback">
              </b-form-input>
              <b-form-invalid-feedback id="lastname-feedback">Debe ingresar el apellido materno</b-form-invalid-feedback>
            </b-form-group>

            <b-form-group id="surname-1" label="Apellido Materno" label-for="surname">
              <b-form-input
                id="surname" 
                name="surname"
                placeholder="Ingresa apellido materno"
                v-model="form.surname"
                v-validate="{ alpha }"
                :state="validateState('surname')"
                aria-describedby="surname-feedback">
              </b-form-input>
              <b-form-invalid-feedback id="surname-feedback">Debe ingresar el apellido materno</b-form-invalid-feedback>
            </b-form-group>

            <!-- Fecha de nacimiento -->
            <!-- v-model="value" -->
            <b-form-group id="date" label="Fecha de nacimiento" label-for="date" description="">
              <b-form-datepicker 
                id="date" 
                class="mb-2" 
                v-model="date" 
                :state="date">
              </b-form-datepicker>
              <b-form-invalid-feedback :state="date">Completa el campo requerido</b-form-invalid-feedback>
            </b-form-group>

            <!-- Correo electronico -->
            <b-form-group id="email-1" label="Email" label-for="email" description="">
              <b-form-input id="email" type="email" placeholder="Ingresa tu correo electronico" v-model="form.email" :state="email"></b-form-input>
              <b-form-invalid-feedback :state="email">
                Completa
              </b-form-invalid-feedback>
              <b-form-valid-feedback :state="email"></b-form-valid-feedback>
            </b-form-group>

            <!-- Numero telefonico -->
            <b-form-group id="phone-1" label="Telefono" label-for="phone" description="">
              <b-form-input 
                id="phone"
                name="phone"
                placeholder="Numero telefonico" 
                v-model="form.phone" 
                v-validate="{required: true, digits: 10}"
                :state="validateState('phone')"
                aria-describedby="phone-feedback"
                @keypress="validarNumero"
                @paste="validarNumero">
              </b-form-input>
              <b-form-invalid-feedback id="phone-feedback">Solo se admite 10 digitos</b-form-invalid-feedback>
            </b-form-group>

            <!-- Fotografia -->
            <b-form-file 
              id="file" 
              accept=".jpg, .png, .gif" 
              placeholder="Escoge la imagen"
              v-validate="{size: 3}" 
              plain>
            </b-form-file>
          </b-col>

          <b-col cols="6">
            <h3>Dirección</h3>
            <!-- Direccion -->
            <b-form-group id="cp-1" label="Codigo Postal" label-for="cp">
              <b-form-input 
                id="cp" 
                name="cp" 
                placeholder="Ingresa tu codigo postal"
                v-model="form.cp" 
                v-validate="{required: true, digits: 5}"
                :state="validateState('cp')"
                aria-describedby="cp-feedback"
                @keypress="validarNumero"
                @paste="validarNumero" >
              </b-form-input>
              <b-form-invalid-feedback id="cp-feedback">Ingresa el codigo postal</b-form-invalid-feedback>
            </b-form-group>

            <b-form-group id="street-1" label="Calle" label-for="street" description="">
              <b-form-input id="street" placeholder="Calle" v-model="form.street" :state="street" ></b-form-input>
              <b-form-invalid-feedback :state="street">
                Completa el campo requerido
              </b-form-invalid-feedback>
              <b-form-valid-feedback></b-form-valid-feedback>
            </b-form-group>

            <b-form-group id="number-1" label="Numero" label-for="number" description="">
              <b-form-input 
                id="number" 
                name="number"
                placeholder="Ingresa el numero donde reside" 
                v-model="form.number" 
                v-validate="{required: true, digits: 5}"
                :state="validateState('number')"
                aria-describedby="number-feedback"
                @keypress="validarNumero"
                @paste="validarNumero">
              </b-form-input>
              <b-form-invalid-feedback id="number-feedback">Completa el campo requerido</b-form-invalid-feedback>
            </b-form-group>

            <b-form-group id="city-1" label="Ciudad" label-for="city" description="">
              <b-form-input 
                id="city" 
                name="city"
                placeholder="Ciudad donde vive" 
                v-model="form.city" 
                v-validate="{ required: true, min: 4, max: 10, alpha }" 
                :state="validateState('city')"
                aria-describedby="city-feedback">
              </b-form-input>
              <b-form-invalid-feedback id="city-feedback">Completa el campo requerido</b-form-invalid-feedback>
            </b-form-group>

          </b-col>
          <b-button id="btn" type="submit" variant="primary">Submit</b-button>
        </b-row>
      </b-container>

    </b-form>
  </div>
</template>

<script>
export default {
  data(){
    return {
      form: {
        name: '',
        lastname: '',
        surname: '',
        phone: '',
      },
    }
  },
  methods: {
    validateState(ref) {
      if (this.veeFields[ref] && (this.veeFields[ref].dirty || this.veeFields[ref].validated)
      ){
    return !this.veeErrors.has(ref);
    }
    return null
    },
    onSubmit() {
      this.$validator.validateAll().then(result => {
        if (!result){
          return
        }
      })
    },
    validarNumero(event) {
      if (!(event.charCode >= 48 && event.charCode <= 57)) {
        event.preventDefault(); // Evita que se ingrese el carácter no deseado
      }
    },
  }
}
</script>

//como aplicar estilos a un componente
<style scoped>
#lastname-1, #name-1, #surname-1, #email-1, #phone-1, #cp-1, #street-1, #number-1, #city-1, #form1, #date{
  margin-top: 8px;
}
#file{
  margin-top: 10px;
}
#btn{
  margin-top: 10px;
  width: 15%;
}

</style>