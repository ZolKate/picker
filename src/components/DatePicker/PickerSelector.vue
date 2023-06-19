<template>
    <v-card-text>
        <v-btn 
            width="100%"
            text
            outlined
            @click = "scroll_up"
        >
            <v-icon>mdi-arrow-up-bold</v-icon>
        </v-btn>
        <v-list
            ref="scroller"
            class="overflow-y-auto" 
            max-height="350"
        >
            <v-list-item-group
                v-model="selectedItem"
            >
                <v-list-item
                    v-for="(item, ind) in items"
                    :key="ind"
                    ref="picker-item"
                >
                    {{ item }}
                </v-list-item>
            </v-list-item-group>
        </v-list>
        <v-btn 
            width="100%"
            text
            outlined
            @click = "scroll_down"
        >
            <v-icon>mdi-arrow-down-bold</v-icon>
        </v-btn>
    </v-card-text>
</template>

<script>
export default{
    props:{
        items: {
            type: Array,
            required: true
        },
        value:{
        }
    },
    data(){
        return {
            selectedItem: this.items.findIndex(item => item == this.value)
        }
    },
    computed: {
        scroll_bias(){
            let scroller = this.get_scroller()
            return scroller.clientHeight * 0.2
        },
    },
    methods:{
        get_scroller() {
            return this.$refs.scroller.$el
        },
        scroll_up(){
            let scroller = this.get_scroller()
            scroller.scrollTo({left: 0, top: scroller.scrollTop - this.scroll_bias, behavior: 'smooth'})
        },
        scroll_down(){
            let scroller = this.get_scroller()
            scroller.scrollTo({left: 0, top: scroller.scrollTop + this.scroll_bias, behavior: 'smooth'})
        }
    },
    watch: {
        selectedItem(val){
            if(val!=undefined) {
                this.$refs['picker-item'][val].$el.scrollIntoView({ behavior: "smooth", block: "center", inline: "nearest" })
                this.$emit("input", this.$refs['picker-item'][val].$el.innerText)
            }
        },
        value(val){
            if(val !== undefined){
                let index = this.items.findIndex(item => item == val)
                this.selectedItem = index
            }
        }
    },
}
</script>