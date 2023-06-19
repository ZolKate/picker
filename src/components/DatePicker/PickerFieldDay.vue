<template>
    <v-text-field 
        v-model="day"
        dark
        flat 
        solo
        hide-details 
        background-color="transparent"
        type="number"
        min="1"
        max="31"
        width = "100px"
    >
    </v-text-field>
</template>

<script>

export default{
    props:{
        value:{
            type: Date
        },
        options:{
            min: int,
            max: int
        }
    },
    data:function() {
        return {
            day: null
    };
}
}
</script>