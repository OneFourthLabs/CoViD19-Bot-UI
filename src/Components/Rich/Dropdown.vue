<template>
    <!-- <div>
        <b-dropdown size="lg"  variant="link" toggle-class="text-decoration-none" no-caret  v-model="querySelection">
            <template v-slot:button-content>
                &#x1f50d;<span class="sr-only">Search</span>
            </template>

            <b-dropdown-item class="dd-options" v-for="option in outlineOptions" :value="option.value" :key="option.id" v-on:click="emitToParent($event)">{{option.text}}</b-dropdown-item>
        </b-dropdown>
    </div> -->


    <div>
        <b-dropdown size="lg"  variant="link" toggle-class="text-decoration-none" no-caret id="dropdown-grouped" text="Dropdown with group" class="m-2">
            <template v-slot:button-content>
                &#x1f50d;<span class="sr-only">Search</span>
            </template>
            
            <b-dropdown-group id="dropdown-group-1" header="Group 1">
                <b-dropdown-item-button v-on:click="emitToParent($event)">How many deaths have occured in Italy over the last 10 days?</b-dropdown-item-button>
                <b-dropdown-item-button>Second Grouped Item</b-dropdown-item-button>
            </b-dropdown-group>

            <b-dropdown-group id="dropdown-group-2" header="Group 2">
                <b-dropdown-item-button>First Grouped item</b-dropdown-item-button>
                <b-dropdown-item-button>Second Grouped Item</b-dropdown-item-button>
            </b-dropdown-group>

            <b-dropdown-divider></b-dropdown-divider>
        </b-dropdown>
    </div>
</template>

<style lang="sass">
.dd-options a
    width: 20.2rem
    word-wrap: break-word !important
    padding: 0.5rem 0.5rem !important
    white-space: unset !important
    line-height: 2

.dropdown-menu
    position: absolute
    will-change: transform
    border-radius: 20px
    // box-shadow: grey 5px 5px
    top: -1.2rem !important
    left: 1rem !important
    transform: translate3d(0px, -252px, 0px)
    background-color: #e4e4e4


</style>



<script>
export default {
    data(){
        return {
            querySelection: '',
            outlineOptions: [
                { id: 0, text: 'How many deaths have occured in Italy over the last 10 days?', value: 'How many deaths have occured in Italy over the last 10 days?' },
                { id: 1, text: 'Which Indian state has the highest number of infected people?', value: 'Which Indian state has the highest number of infected people?' },
                { id: 2, text: 'Show a plot of number of infected people in Maharashtra', value: 'Show a plot of number of infected people in Maharashtra' },
                { id: 3, text: 'Draw a line plot of number of people recovered in China over the month of March.', value: 'Draw a line plot of number of people recovered in China over the month of March.' }
            ]
        }
    },
    // props: ['query-msg'],
    methods: {
        // Define the method that emits data to the parent as the first parameter to `$emit()`.
        // This is referenced in the <template> call in the parent. The second parameter is the payload.
        emitToParent (event) {
            // console.log(event.target.text);
            this.$emit('childToParent', event.target.text)
        }
    }
}
</script>