<template>
    <div>
        <div class="form-group col-sm-10" >
            <label for="Name">Name</label>
            <input type="text" class="form-control" id="FName" v-model.trim="$parent.$v.fname.$model" placeholder="Enter Your Name">
             <slot></slot>
        </div>
    </div>
</template>
<script>
export default {
    name: 'input-name',
   
};
</script>