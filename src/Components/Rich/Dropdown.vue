<template>
    <!-- <div>
        <b-dropdown size="lg"  variant="link" toggle-class="text-decoration-none" no-caret  v-model="querySelection">
            <template v-slot:button-content>
                &#x1f50d;<span class="sr-only">Search</span>
            </template>

            <b-dropdown-item class="dd-options" v-for="option in outlineOptions" :value="option.value" :key="option.id" v-on:click="emitToTophead($event)">{{option.text}}</b-dropdown-item>
        </b-dropdown>
    </div> -->

    <div>
        <!-- <div id="myNav" class="overlay" v-on:click="navClick($event)">
            <a href="javascript:void(0)" class="closebtn" v-on:click="closeNav($event)">&times;</a>   
        </div> -->

        <!-- <b-dropdown size="lg" variant="link" toggle-class="text-decoration-none" no-caret id="dropdown-grouped" text="Dropdown with group" class="m-2"> -->
        <b-dropdown id="dropdown-grouped" text="Sample Queries" class="m-2">
            <!-- <template v-slot:button-content>
                <div v-on:click="openNav($event)">
                    &#x1f50d;<span class="sr-only">Search</span>
                </div>
            </template> -->

                <b-dropdown-group id="dropdown-group-1" header="Stats">
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">How many deaths have occured in Italy over the last 10 days?</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Which Indian state has the highest number of infected people?</b-dropdown-item-button>
                </b-dropdown-group>

                <b-dropdown-divider></b-dropdown-divider>

                <b-dropdown-group id="dropdown-group-2" header="Plots">
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Show a plot of number of infected people in Maharashtra</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Draw a line plot of number of people recovered in China over the month of March.</b-dropdown-item-button>
                </b-dropdown-group>

                <b-dropdown-divider></b-dropdown-divider>

                <b-dropdown-group id="dropdown-group-3" header="Recommendations">
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Should I spray alcohol on my body</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Should I take a flu shot</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Should I rinse my noise</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Is it safe to travel by air</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Is it safe to sit in an air conditioned office </b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Is it safe to go for a walk</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Should I eat garlic</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Should I take H1NI vaccine</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Should I take a flu shot</b-dropdown-item-button>
                </b-dropdown-group>

                <b-dropdown-divider></b-dropdown-divider>

                <b-dropdown-group id="dropdown-group-4" header="Info">
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">What is coronavirus</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">How long does the treatment take</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">How long should I stay in quarantine</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">How long will it take for me to fully recover</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">How long does the virus survive on plastic</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">How long does the virus survive on glass</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">How long does the virus survive on metal surfaces</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Can the disease spread from an asymptomatic person</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Can the disease spread from soil</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Can the disease spread from water</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">What is the difference between epidemic and pandemic</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">What is the difference between isolation and quarantine</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">What is the difference between MERS and SARS</b-dropdown-item-button>
                </b-dropdown-group>

                <b-dropdown-divider></b-dropdown-divider>

                <b-dropdown-group id="dropdown-group-5" header="Procedures">
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">How to disinfect my phone</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">How to disinfect my car</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">How to disinfect my room</b-dropdown-item-button>
                </b-dropdown-group>


                <!-- <b-dropdown-divider></b-dropdown-divider>

                <b-dropdown-group id="dropdown-group-2" header="Plots">
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)"></b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)"></b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)"></b-dropdown-item-button>
                </b-dropdown-group>

                <b-dropdown-divider></b-dropdown-divider> -->
        </b-dropdown>
    </div>
</template>

<style lang="sass">
.m-2
    margin-left: 1.5rem !important

.sr-only
    margin-left: 21.5rem

.dd-options button
    width: var(--overlay-dd-width)
    word-wrap: break-word !important
    padding: 0.5rem 1.7rem !important
    white-space: unset !important
    line-height: 2
    color: var(--text-secondary)
    text-align: justify
    text-justify: inter-word

.dd-options button:hover
    background-color: var(--dd-hoover-bg-color)

.dropdown-menu
    position: absolute
    will-change: transform
    // border-radius: 20px
    box-shadow: var(--box-shadow-color) 0px 1px 4px 1px
    top: var(--overlay-dd-top) !important
    left: .2rem !important
    transform: translate3d(0px, -252px, 0px)
    background-color: var(--background)
    overflow-y: scroll
    height: var(--overlay-dd-height)

.dropdown-header
    padding: 0.5rem 1.3rem
    font-size: 1.2rem
    color: var(--text)

.dropdown-divider 
    border-top: 1px solid #bbbbbb !important

.overlay 
    height: 100%
    width: 0
    display: none
    position: fixed
    z-index: 1
    top: 0
    left: 0
    background-color: var(--overlay-background-color)
    background-color: var(--overlay-background-color-a)
    overflow-x: hidden
    transition: 0.5s

.overlay a 
    padding: 8px
    text-decoration: none
    font-size: 36px
    color: var(--text)
    display: block
    transition: 0.3s

.overlay .closebtn 
    position: absolute
    top: var(--overlay-close-top)
    right: var(--overlay-close-right)
    font-size: var(--overlay-close-font-size)
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
        emitToTophead (event) {
            // alert(event.target.innerHTML);
            this.$emit('dropdownToTophead', event.target.innerHTML)
            // this.closeNav(event)
        },
        // openNav(event) {
        //     console.log(event);
        //     document.getElementById("myNav").style.width = "100%";
        //     document.getElementById("myNav").style.display = "block";
        // },
        // closeNav(event) {
        //     console.log(event);
        //     document.getElementById("myNav").style.width = "0%";
        //     setTimeout(function(){ 
        //         document.getElementById("myNav").style.display = "none";
        //         document.getElementById("myNav").style.width = "100%";
        //     }, 500);
        // },
        // navClick(event) {
        //     const element = document.querySelector("#dropdown-grouped");
        //     // alert(element.classList.contains("show"));
        //     // if(element.classList.contains("show") == false) {
        //         this.closeNav(event);
        //     // }
        // }
    }
}
</script>