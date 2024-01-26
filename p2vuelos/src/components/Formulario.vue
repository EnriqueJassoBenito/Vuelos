<template>
  <div>
    <h1 class="text-center">Hola esto es un formulario</h1>

    <b-form>

      <b-container class="">
        <b-row >
          <b-col cols="6">
            <h3>Datos</h3>
            <!-- Nombre completo -->
            <b-form-group id="name-1" label="Nombre" label-for="name" description="">
              <b-form-input id="name" placeholder="Ingresa el nombre" v-model="form.name" :state="name"></b-form-input>
              <b-form-invalid-feedback :state="name">
                Completa el campo requerido
              </b-form-invalid-feedback>
              <b-form-valid-feedback :state="name"></b-form-valid-feedback>
            </b-form-group>

            <b-form-group id="lastname-1" label="Apellido Paterno" label-for="lastname" description="">
              <b-form-input id="lastname" placeholder="Ingresa apellido paterno" v-model="form.lastname" :state="lastname"></b-form-input>
              <b-form-invalid-feedback :state="lastname">
                Completa el campo requerido
              </b-form-invalid-feedback>
              <b-form-valid-feedback :state="lastname"></b-form-valid-feedback>
            </b-form-group>

            <b-form-group id="surname-1" label="Apellido Materno" label-for="surname" description="">
              <b-form-input id="surname" placeholder="Ingresa apellido materno" ></b-form-input>
            </b-form-group>

            <!-- Fecha de nacimiento -->
            <!-- v-model="value" -->
            <b-form-group id="date" label="Fecha de nacimiento" label-for="date" description="">
              <b-form-datepicker id="date" class="mb-2" v-model="date" :state="date"></b-form-datepicker>
              <b-form-invalid-feedback :state="date">
                Completa el campo requerido
              </b-form-invalid-feedback>
              <b-form-valid-feedback :state="date"></b-form-valid-feedback>
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
              <b-form-input id="phone" type="number" placeholder="Numero telefonico" v-model="form.phone" :state="phone"></b-form-input>
              <b-form-invalid-feedback :state="phone">
                Completa el campo requerido
              </b-form-invalid-feedback>
              <b-form-valid-feedback :state="phone"></b-form-valid-feedback>
            </b-form-group>

            <!-- Fotografia -->
            <b-form-file id="file" accept=".jpg, .png, .gif" placeholder="Escoge la imagen" plain></b-form-file>
          </b-col>

          <b-col cols="6">
            <h3>Dirección</h3>
            <!-- Direccion -->
            <b-form-group id="cp-1" label="Codigo Postal" label-for="cp" description="">
              <b-form-input id="cp" type="number" placeholder="Ingresa tu codigo postal" v-model="form.cp" :state="cp" ></b-form-input>
              <b-form-invalid-feedback :state="cp">
                Completa el campo requerido
              </b-form-invalid-feedback>
              <b-form-valid-feedback></b-form-valid-feedback>
            </b-form-group>

            <b-form-group id="street-1" label="Calle" label-for="street" description="">
              <b-form-input id="street" placeholder="Calle" v-model="form.street" :state="street" ></b-form-input>
              <b-form-invalid-feedback :state="street">
                Completa el campo requerido
              </b-form-invalid-feedback>
              <b-form-valid-feedback></b-form-valid-feedback>
            </b-form-group>

            <b-form-group id="number-1" label="Numero" label-for="number" description="">
              <b-form-input id="number" placeholder="Ingresa el numero donde reside" v-model="form.number" :state="number" ></b-form-input>
              <b-form-invalid-feedback :state="number">
                Completa el campo requerido
              </b-form-invalid-feedback>
              <b-form-valid-feedback></b-form-valid-feedback>
            </b-form-group>

            <b-form-group id="city-1" label="Ciudad" label-for="city" description="">
              <b-form-input id="city" placeholder="Ciudad donde vive" v-model="form.city" :state="city"></b-form-input>
              <b-form-invalid-feedback :state="city">
                Completa el campo requerido
              </b-form-invalid-feedback>
              <b-form-valid-feedback></b-form-valid-feedback>
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
        email: '',
        phone: '',
        cp: '',
        street: '',
        number: '',
        city: '',
      },
    }
  },
  computed: {
    name(){
      return this.form.name.length > 4 && this.form.name.length < 30 
    },
    lastname(){
      return this.form.lastname.length > 4 && this.form.lastname.length < 10 
    },
    email(){
      return this.form.email.includes('@') && this.form.email.includes('.')
    },
    phone(){
      return this.form.phone.length > 9 && this.form.phone.length < 11
    },
    cp(){
      return this.form.cp.length > 4 && this.form.cp.length < 6
    },
    street(){
      return this.form.street.length > 4 && this.form.street.length < 30
    },
    number(){
      return this.form.number.length > 0 && this.form.number.length < 5
    },
    city(){
      return this.form.city.length > 4 && this.form.city.length < 30
    },
    date(){
      return this.form.date ? true : false
    }
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