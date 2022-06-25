<template>
    <div>
        <div class="form-group col-sm-10" >
            <label for="Name">Name</label>
            <input type="text" class="form-control" id="FName" :class="{ 'form-group--error':$parent.validationsStatus($parent.$v.fname) }" v-model.trim="$parent.$v.fname.$model" placeholder="Enter Your Name">
             <slot></slot>
        </div>
    </div>
</template>
<script>
export default {
    name: 'input-name',
    props:{
        fname : String
    },
   
};
</script>