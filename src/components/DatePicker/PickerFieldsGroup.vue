<template>
    <v-card-title
        class="green white--text"

    >
        <v-row align="center">
            <PickerFieldMonth v-model="month"/>
            <PickerFieldYear v-model="year"/>
        </v-row>
    </v-card-title>
</template>

<script>
import PickerFieldMonth from './PickerFieldMonth.vue';
import PickerFieldYear from './PickerFieldYear.vue';

export default{
    props: ["value"],
    data: () => ({
        
    }),
    computed: {
        day: {
            set(value) {
                this.value.setDate(value);
            },
            get() {
                return this.value.getDate();
            }
        },
        month: {
            set(value) {
                let date = new Date(this.value.setMonth(value));
                this.$emit('input', date);
            },
            get() {
                return this.value.getMonth();
            }
        },
        year: {
            set(value) {
                let date = new Date(this.value.setFullYear(value));
                this.$emit('input', date);  
            },
            get() {
                return this.value.getFullYear();
            }
        }
    },
    watch: {},
    components: { PickerFieldMonth, PickerFieldYear }
}
</script>
