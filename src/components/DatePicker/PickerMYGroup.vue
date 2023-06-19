<template>
    <div style="display: flex;">
        <PickerSelector
            :items="[2016,2017,2018,2019,2020,2021,2022,2023,2024,2025]"
            v-model="year"
        />
        <PickerSelector
            :items="months"
            v-model="month"
        />
    </div>
</template>

<script>
import PickerSelector from './PickerSelector.vue'

export default{
    props: {
        value: {
            type: Date
        }
    },
    data: ()=>({
        months: ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December']
    }),
    computed:{
        year:{
            set(value){
                let date = new Date(this.value.setFullYear(value))
                this.$emit('input', date)
            },
            get(){
                return this.value.getFullYear()
            }
            
        },
        month:{
            set(value){
                let date = new Date( this.value.setMonth(this.months.findIndex(item => item == value)))
                this.$emit('input', date)
            },
            get(){
                return this.months[this.value.getMonth()]
            }
        }
    },
    methods:{
    },
    watch: {
        value(val){
            if(val !== undefined)
                this.date = this.value
        },
    },
    components:{
        PickerSelector
    }
}
</script>