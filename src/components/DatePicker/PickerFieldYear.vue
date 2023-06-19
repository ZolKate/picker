<template>
    <v-text-field
        v-model="year"
        dark
        flat
        solo
        hide-details 
        background-color="transparent"
        type="number"
        min="2000"
        max="2050"
        step="1"
        width = "100"
    >
    </v-text-field>
</template>

<script>
export default{
    props:{
        value: {
            type: Number
        }
    },
    computed:{
        year:{
            set(value){
                this.$emit('input', value)
            },
            get(){
                return this.value
            }
        } 
    }
}
</script>