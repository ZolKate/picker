<template>
    <v-card
        class="picker_wrapper"
    >
        <PickerFieldsGroup v-model="date" />
        <v-card-actions class="picker_action">
            <PickerMYGroup v-model="date"/>
            <PickerTable v-model="date"/>
        </v-card-actions>
    </v-card>
</template>

<script>
import PickerFieldsGroup from './PickerFieldsGroup.vue';
import PickerMYGroup from './PickerMYGroup.vue';
import PickerTable from './PickerTable.vue';

export default{
    name: "DatePicker",
    data: () => ({
        date: new Date()
    }),
    computed:{
    },
    components: {
        PickerFieldsGroup,
        PickerMYGroup,
        PickerTable
    }
}
</script>

<style>
    .picker_action{
        display: flex;
    }
</style>