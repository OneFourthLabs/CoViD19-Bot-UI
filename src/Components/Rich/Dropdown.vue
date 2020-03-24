<template>
    <div>
        <b-dropdown id="dropdown-1" text="Select query" class="m-md-2" v-model="outlineOptions">
            <b-dropdown-item v-for="option in outlineOptions" :value="option.value" @click="onClick(option.value)">{{option.text}}</b-dropdown-item>
            <!-- <b-dropdown-divider /> -->
        </b-dropdown>
    </div>
</template>

<script>
export default {
    data(){
        return {
            outlineOptions: [
                { text: 'What is coronavirus', value: 'What is coronavirus' },
                { text: 'What is coronavirus', value: 'What is coronavirus' },
                { text: 'What is coronavirus', value: 'What is coronavirus' }
            ]
        }
    },
    props: ['query-msg'],
    methods: {
        onClick(text){
            alert(text);
            // this.outlineOptions = text;
            // Close the menu and (by passing true) return focus to the toggle button
            // this.$refs.dropdown.hide(true)
        }
    }
}
</script>