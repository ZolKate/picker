<template>
    <table>
        <tbody>
            <tr>
                <td>{{ daysInMonth }}</td>
            </tr>
        </tbody>
    </table>
</template>

<script>
export default{
    props: ["value"],
    data: () => ({

    }),
    computed:{
        daysInMonth(){
            return new Date(this.value.getFullYear(), this.value.getMonth(), 0).getDate()
        }
    },
    
}
</script>