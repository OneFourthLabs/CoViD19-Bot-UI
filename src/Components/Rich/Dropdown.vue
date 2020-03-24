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

            <b-dropdown-group id="dropdown-group-1" header="Stats">
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">How many deaths have occured in Italy over the last 10 days?</b-dropdown-item-button>
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">Which Indian state has the highest number of infected people?</b-dropdown-item-button>
            </b-dropdown-group>

            <b-dropdown-divider></b-dropdown-divider>

            <b-dropdown-group id="dropdown-group-2" header="Plots">
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">Show a plot of number of infected people in Maharashtra</b-dropdown-item-button>
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">Draw a line plot of number of people recovered in China over the month of March.</b-dropdown-item-button>
            </b-dropdown-group>

            <b-dropdown-divider></b-dropdown-divider>

            <b-dropdown-group id="dropdown-group-2" header="What is the difference between A and B?">
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">What is the difference between epidemic and pandemic?</b-dropdown-item-button>
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">What is the difference between isolation and quarantine?</b-dropdown-item-button>
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">What is the difference between MERS and SARS?</b-dropdown-item-button>
            </b-dropdown-group>

            <b-dropdown-divider></b-dropdown-divider>

            <b-dropdown-group id="dropdown-group-2" header="Should I do X ?">
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">Should I spray alcohol on my body ?</b-dropdown-item-button>
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">Should I take a flu shot ?</b-dropdown-item-button>
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">Should I rinse my noise ?</b-dropdown-item-button>
            </b-dropdown-group>

            <b-dropdown-divider></b-dropdown-divider>

            <b-dropdown-group id="dropdown-group-2" header="How long does X last ?">
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">How long does the treatment take ?</b-dropdown-item-button>
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">How long should I stay in quarantine ?</b-dropdown-item-button>
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">How long will it take for me to fully recover ?</b-dropdown-item-button>
            </b-dropdown-group>

            <b-dropdown-divider></b-dropdown-divider>

            <b-dropdown-group id="dropdown-group-2" header="How to disinfect X ?">
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">How to disinfect my phone ?</b-dropdown-item-button>
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">How to disinfect my car ?</b-dropdown-item-button>
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">How to disinfect my room ?</b-dropdown-item-button>
            </b-dropdown-group>

            <b-dropdown-divider></b-dropdown-divider>

            <b-dropdown-group id="dropdown-group-2" header="Is it safe to do X ?">
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">Is it safe to travel by air ?</b-dropdown-item-button>
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">Is it safe to sit in an air conditioned office ?</b-dropdown-item-button>
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">Is it safe to go for a walk ?</b-dropdown-item-button>
            </b-dropdown-group>

            <b-dropdown-divider></b-dropdown-divider>

            <b-dropdown-group id="dropdown-group-2" header="How long does the virus survive on X?">
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">How long does the virus survive on plastic ?</b-dropdown-item-button>
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">How long does the virus survive on glass ?</b-dropdown-item-button>
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">How long does the virus survive on metal surfaces ?</b-dropdown-item-button>
            </b-dropdown-group>

            <b-dropdown-divider></b-dropdown-divider>

            <b-dropdown-group id="dropdown-group-2" header="Does disease spread through X?">
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">Can the disease spread from an asymptomatic person ?</b-dropdown-item-button>
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">Can the disease spread from soil ?</b-dropdown-item-button>
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">Can the disease spread from water ?</b-dropdown-item-button>
            </b-dropdown-group>

            <b-dropdown-divider></b-dropdown-divider>

            <b-dropdown-group id="dropdown-group-2" header="Should I consume X ?">
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">Should I eat garlic ?</b-dropdown-item-button>
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">Should I take H1NI vaccine ?</b-dropdown-item-button>
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)">Should I take a flu shot ?</b-dropdown-item-button>
            </b-dropdown-group>

            <!-- <b-dropdown-divider></b-dropdown-divider>

            <b-dropdown-group id="dropdown-group-2" header="Plots">
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)"></b-dropdown-item-button>
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)"></b-dropdown-item-button>
                <b-dropdown-item-button class="dd-options" v-on:click="emitToParent($event)"></b-dropdown-item-button>
            </b-dropdown-group>

            <b-dropdown-divider></b-dropdown-divider> -->
        </b-dropdown>
    </div>
</template>

<style lang="sass">
.dd-options button
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
    overflow-y: scroll
    height: 16rem

.dropdown-header
    padding: 0.5rem 0.5rem
    font-size: 1.2rem

.dropdown-divider 
    border-top: 1px solid #bbbbbb !important
</style>



<script>
export default {
    data(){
        return {
            querySelection: '',
            // outlineOptions: [
            //     { id: 0, text: 'How many deaths have occured in Italy over the last 10 days?', value: 'How many deaths have occured in Italy over the last 10 days?' },
            //     { id: 1, text: 'Which Indian state has the highest number of infected people?', value: 'Which Indian state has the highest number of infected people?' },
            //     { id: 2, text: 'Show a plot of number of infected people in Maharashtra', value: 'Show a plot of number of infected people in Maharashtra' },
            //     { id: 3, text: 'Draw a line plot of number of people recovered in China over the month of March.', value: 'Draw a line plot of number of people recovered in China over the month of March.' }
            // ]
        }
    },
    // props: ['query-msg'],
    methods: {
        // Define the method that emits data to the parent as the first parameter to `$emit()`.
        // This is referenced in the <template> call in the parent. The second parameter is the payload.
        emitToParent (event) {
            // alert(event.target.innerHTML);
            this.$emit('childToParent', event.target.innerHTML)
        }
    }
}
</script>