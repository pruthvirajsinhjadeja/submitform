<template>
    <div>
        <div class="form-group col-sm-10" >
            <label for="MobileNumber">Mobile Number <span class="text-danger">*</span></label>
            <input  class="form-control" type="number" v-model.trim="$parent.$v.mobileNumber.$model"  placeholder="Enter Your Mobile">
             <slot></slot>
        </div>
    </div>
</template>
<script>
export default {
    name: 'input-mobile-number',
};
</script>