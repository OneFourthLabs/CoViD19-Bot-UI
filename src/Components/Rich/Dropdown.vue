<template>
    <div>
        <b-dropdown id="dropdown-1" text="Select query" class="m-md-2" v-model="querySelection">
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
                { id: 0, text: 'What is coronavirus', value: 'What is COVID-19' },
                { id: 1, text: 'What is SARS', value: 'What is SARS' },
                { id: 2, text: 'What is MERS', value: 'What is MERS' }
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