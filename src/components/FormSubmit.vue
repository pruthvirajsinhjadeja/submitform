<template>
  <div class="card center" style="width: 50%;text-align: left;margin-left: 25%;">
    <div class="card-header">
      <h1>{{ msg }}</h1>
    </div>
    <!-- {{$v}} -->
    <form class="center" style="margin-bottom: 10px;">
      <div>
        <input-name>
          <span class="text-danger" v-if="!$v.fname.required && isNameErrorVisible">
            The Name is required
          </span>
        </input-name>
        <input-email>
          <span class="text-danger" v-if="!$v.email.required && isEmailErrorVisible">
            The EMail is required
          </span>
          <span class="text-danger" v-if="!$v.email.email">
            Please enter Valid Email
          </span>
        </input-email>
        <input-date-of-birth>
          <span class="text-danger" v-if="!$v.DateOfBirth.required && isDateOFBirthErrorVisible">
            The Date Of birth is required
          </span>
        </input-date-of-birth>
        <input-gender>
          <span class="text-danger" v-if="!$v.gender.required && isGenderErrorVisible">The Gender is required</span>
        </input-gender>

        <input-mobile-number>
          <span class="text-danger" v-if="!$v.mobileNumber.required && isMobileErrorVisible">The Mobile Number is required</span>
          <span class="text-danger" v-if="!$v.mobileNumber.minLength">The have at least
            {{ $v.mobileNumber.$params.minLength.min }} digit</span>
          <span class="text-danger" v-if="!$v.mobileNumber.maxLength">The have at least
            {{ $v.mobileNumber.$params.maxLength.max }} digit</span>
        </input-mobile-number>
        <button type="submit" class="btn btn-primary" style="margin-left: 40%;" @click.prevent="submit">Submit</button>
      </div>
    </form>
  </div>
</template>

<script>
import FullName from './Input_Name.vue'
import EmailAddress from './Input_email.vue'
import DateOfBirth from './Input_Date_of_birth.vue'
import Gender from './Input_Gender.vue'
import MobileNumber from './Input_Mobile_number.vue'
import { required, email, numeric, minLength, maxLength } from 'vuelidate/lib/validators'
export default {
  name: 'FormSubmit',
  props: {
    msg: String
  },
  validations: {
    fname: { required },
    email: { required, email },
    DateOfBirth: { required },
    gender: { required },
    mobileNumber: {
      required,
      numeric,
      minLength: minLength(10),
      maxLength: maxLength(12)
    }
  },
  data() {
    return {
      fname: '',
      email: '',
      DateOfBirth: '',
      gender: '',
      mobileNumber: '',
      isNameErrorVisible: false,
      isEmailErrorVisible: false,
      isDateOFBirthErrorVisible: false,
      isGenderErrorVisible: false,
      isMobileErrorVisible:false
    };
  },
  components: {
    'input-name': FullName,
    'input-email': EmailAddress,
    'input-date-of-birth': DateOfBirth,
    'input-gender': Gender,
    'input-mobile-number': MobileNumber
  },
  methods: {
    validationsStatus: function (validation) {
      return typeof validation != 'undefined' ? validation.$error : false;

    },
    submit: function () {
      let self = this;
      this.$v.$touch();
      if (this.$v.$pending || this.$v.$error) {
        self.isNameErrorVisible = true;
        self.isEmailErrorVisible = true;
        self.isDateOFBirthErrorVisible = true;
        self.isGenderErrorVisible = true;
        self.isMobileErrorVisible = true;
        return;
      }
      console.log(this.fname);
      console.log(this.email);
      console.log(this.DateOfBirth);
      console.log(this.gender);
      console.log(this.mobileNumber);
    },
  },
}
</script>


