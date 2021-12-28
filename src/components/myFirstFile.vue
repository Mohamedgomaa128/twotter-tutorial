<template>
    <h1>{{ msg }}</h1>
    <h1>this is my first vue after returning to web dev</h1>
</template>


<script>
export default {
    name: 'firstVue',
    props: {
        msg: String
    }
}
</script>

<!-- scoped to limit css to this component only-->
<style scoped> 
h1 {
    margin : 50px 0 0;
}
</style>

