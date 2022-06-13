<template>
    <div >
        <div class="form-group col-sm-10" >
            <label for="FName">Date Of Birth</label>
            <DatePicker format="DD/MM/YYYY" class="col-sm-10" :class="{'is-invalid': $parent.validationsStatus($parent.$v.DateOfBirth)}" placeholder="please select date" v-model.trim="$parent.$v.DateOfBirth.$model"/>
        </div>
    </div>
</template>
<script>
import DatePicker from 'vue2-datepicker';
import 'vue2-datepicker/index.css';
export default {
    name: 'DOB',
    components:{
            DatePicker
    },

    data() {
        return {
              DOB: '',
        };
    },

   
};
</script>