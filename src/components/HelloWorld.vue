<template>
  <div class="hello container">
              <form @submit.prevent="submitForm">

  <div class="col-md-11 mb-3">
    <label >Nested A</label>
    <input  class="form-control "  v-model.trim="$v.profile.name.$model"/>
  <div class="invalid-feedback" v-if="!$v.profile.name.required && $v.profile.name.$dirty" >Field is required.</div>
  </div>
  
  <div class="col-md-11 mb-3">
    <label class="form__label">Nested B</label>
    <input class="form-control"  v-model.trim="$v.profile.address.$model"/>
  <div class="text-danger" v-if="!$v.profile.address.required && $v.profile.address.$dirty" >Field is required.</div>
  </div>
  <div class="form-group" :class="{ 'form-group--error': $v.profile.$error }"></div>
  <div class="error" v-if="$v.profile.$error">Form is invalid.</div>
<button type="submit"  class="btn btn-primary mt-2" >submit</button>
          </form>

  </div>
</template>

<script>
import {
  required,
} from "vuelidate/lib/validators";
export default {
  name: 'HelloWorld',
 data() {
    return {
      profile: {
        name: '',
        address: ''
      }
    }
  },
  validations: {
    profile: {
    name: {
        required
      },
      address: {
        required
      }
    }
  },
  methods: {
       submitForm() {
      this.$v.$touch();

      if (!this.$v.$invalid) {
      //logic
      // this.setDone('second', 'third')
console.log("working")
}else{
  console.log("not")
}
      }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
