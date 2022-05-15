<template>
<div class="row">
    <div class="col-12 col-md-4 m-auto ">
         <div class="input-group mt-5 mb-5 search-bar">
        <input type="text" class="form-control" placeholder="Search any coin!" aria-label="" aria-describedby="">
        <div class="input-group-append">
            <button class="btn btn-outline-secondary" type="button"> <i class="fas fa-search"></i></button>
        </div>
    </div>
    </div>
</div>
   
</template>

<script>
export default {
    name: 'SearchBar',
}
</script>

<style scope>


.btn-outline-secondary {
    background-color: #5a55d2 !important;
    border-color: #5a55d2 !important;
}

.fa-search {
    color: white !important;

}
</style>
