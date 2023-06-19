<template>
    <v-select
            v-model="month"
            :items = "items"
            dark
            flat 
            solo
            hide-details 
            background-color="transparent"
            type="text"
            width = "100px"
        >
    </v-select>
</template>

<script>

export default{
    props: {
        value:{
            type: Number
        }
    },
    data: ()=>({
       
        items: ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"],
    }),
    computed:{
        month:{
            set(value){
                this.$emit('input', this.items.findIndex(item => item == value))
            },
            get(){
                return this.items[this.value]
            }
        } 
    }
}
</script>