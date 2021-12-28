<template>
    <div class="em" @click="favouriteEmail(email.id)">
        from: <strong>{{ from }}</strong><br>
        to: <strong>{{ to }}</strong><br>
        subject: <strong>{{ subject }}</strong>
    </div>
</template>


<script>
export default {
    name: "email",
    props: {
        id:{
            type: Number,
            required: true
        },
        from: {
            type: String,
            required: true
        },
        to: {
            type: String,
            required: true
        },
        subject: {
            type: String,
            required: true
        }
    },
    methods: {
        favouriteEmail(id){
            this.$emit('favEmail', id);
        }
    }
}
</script>


<style scoped>
.em {
    padding: 20px;
    background-color: white;
    border-radius: 5px;
    border: 1px solid #DFE3E8;
    box-sizing: border-box;
    cursor: pointer;
    transition: all 0.25s ease;
}

.em:hover {
    transform: scale(1.1, 1.1);
}


</style>