<template>
    <div>
        <div class="form-group col-sm-10">
            <label for="Email">Email address <span class="text-danger">*</span></label>
            <input type="email" v-model.trim="$parent.$v.email.$model"  class="form-control" id="Email" placeholder="Enter email" >
             <slot></slot>
        </div>
    </div>
</template>
<script>
export default {
    name: 'input-email',
};
</script>