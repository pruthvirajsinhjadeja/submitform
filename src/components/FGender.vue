<template>
    <div>
        <div class="form-group col-sm-12">
            <label for="FGender">Gender <span class="text-danger">*</span></label>
            <select class="form-control col-sm-10" id="FGender" v-model.trim="$parent.$v.gender.$model">
                <option value="">Select Gender</option>
                <option>Male</option>
                <option>Female</option>
               
            </select>
        </div>
    </div>
</template>
<script>
export default {
    name: 'FGender',

    data() {
        return {
            gender : '',
        };
    },

  
};
</script>
