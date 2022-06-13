<template>
  <div class="card center" style="width: 50%;text-align: left;margin-left: 25%;">
    <div class="card-header">
      <h1>{{ msg }}</h1>
    </div>
      <!-- {{$v}} -->
    <form class="center" style="margin-bottom: 10px;">
      <div>
        <FName ></FName>
        <span  class="text-danger" v-if="!$v.fname.required">The Name is required</span>
        <EmaiAdd  ></EmaiAdd>
        <span  class="text-danger" v-if="!$v.email.required">The EMail is required</span>
        <span  class="text-danger" v-if="!$v.email.email">Please enter Valid Email</span>
        <DOB></DOB>
        <span  class="text-danger" v-if="!$v.DateOfBirth.required">The Date Of birth  is required</span>
        <Gender></Gender>
        <span  class="text-danger" v-if="!$v.gender.required">The Gender  is required</span>
        <MobileNumber ></MobileNumber>
         <span  class="text-danger" v-if="!$v.mobileNumber.required">The Mobile  Number is required</span><br/>
         <span  class="text-danger" v-if="!$v.mobileNumber.minLength">The have at least {{$v.mobileNumber.$params.minLength.min}} digit</span><br/>
           <span  class="text-danger" v-if="!$v.mobileNumber.maxLength">The have at least {{$v.mobileNumber.$params.maxLength.max}} digit</span><br/>
        <button type="submit" class="btn btn-primary" style="margin-left: 40%;" @click.prevent="submit">Submit</button>
      </div>
    </form>
  </div>
</template>

<script>
import FName from './FName.vue'
import EmaiAdd from './EmaiAdd.vue'
import DOB from './DOB'
import Gender from './FGender'
import MobileNumber from './MobileNumber'
import {required, email , numeric , minLength ,maxLength} from 'vuelidate/lib/validators'
export default {
  name: 'FormSubmit',
  props: {
    msg: String
  },
  validations:{
        fname : {required},
        email : {required, email},
        DateOfBirth : {required},
        gender:{required},
        mobileNumber : {
          required,
          numeric,
          minLength: minLength(1),
          maxLength: maxLength(12)
        }


  },
  data() {
    return {
      fname: '',
      email:'',
      DateOfBirth:'',
      gender:'',
      mobileNumber:''
    };
  },
  components: {
    FName,
    EmaiAdd,
    DOB,
    Gender,
    MobileNumber
  },
  methods:{
    validationsStatus:function(validation){
      return typeof validation != 'undefined' ? validation.$error : false;

    },
    submit:function(){
      this.$v.$touch();
      if(this.$v.$pending || this.$v.$error) return;
          // alert('Data Submited');
          console.log(this.fname);
          console.log(this.email);
          console.log(this.DateOfBirth);
          console.log(this.gender);
          console.log(this.mobileNumber);

    },
    
  },
 created(){
  console.log(this.fname)
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
