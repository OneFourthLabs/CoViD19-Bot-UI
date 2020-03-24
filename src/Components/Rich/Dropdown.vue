<template>
    <div>
        <b-dropdown size="lg"  variant="link" toggle-class="text-decoration-none" no-caret  v-model="querySelection">
            <template v-slot:button-content>
                &#x1f50d;<span class="sr-only">Search</span>
            </template>


        <!-- <b-dropdown id="dropdown-offset" offset="25" dropup block menu-class="w-100" text="Select query" variant="dark" class="m-md-2" v-model="querySelection"> -->
            <b-dropdown-item v-for="option in outlineOptions" :value="option.value" :key="option.id" v-on:click="emitToParent($event)">{{option.text}}</b-dropdown-item>
            <!-- <b-dropdown-divider /> -->
        </b-dropdown>
    </div>
</template>

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