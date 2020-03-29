<template>
    <div>
        <b-dropdown id="dropdown-grouped" text="Queries" class="m-2">

            <transition name="with-mode-fade" mode="out-in">
                <div v-if="cat_on">
                    <b-dropdown-group header="Select Category" style="font-weight: bold;"></b-dropdown-group>
                    <b-dropdown-divider></b-dropdown-divider>
                    <b-dropdown-group key="on" @click="traversCat('C', 'cat_on', 'subcat_1_on')" header="Stats" class="dd-options-parent dd-sm"></b-dropdown-group>
                </div>
                
                <b-dropdown-group v-else-if="subcat_1_on" key="off" @click="traversCat('S', 'cat_on', 'subcat_1_on')" id="dropdown-group-1" header="< Back to Category" class="dd-options-parent">
                    <b-dropdown-divider></b-dropdown-divider>
                  
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">How many recovered in India in March?</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">What is the number of deaths in New York?</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Which state in India has the maximum number of cases?</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">How many cases in India since last week?</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">How many cases was confirmed in Tamil Nadu since last 5 days?</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">How many cases in Maharastra from March 11 to March 20?</b-dropdown-item-button>
                </b-dropdown-group>
            </transition>

            <transition name="with-mode-fade" mode="out-in">
                <b-dropdown-group v-if="cat_on" key="on" @click="traversCat('C', 'cat_on', 'subcat_2_on')" header="Plots" class="dd-options-parent dd-sm"></b-dropdown-group>

                <b-dropdown-group v-else-if="subcat_2_on" key="off" @click="traversCat('S', 'cat_on', 'subcat_2_on')" id="dropdown-group-2" header="< Back to Category" class="dd-options-parent">
                    <b-dropdown-divider></b-dropdown-divider>

                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Plot the total number of cases in Italy from January.</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Draw a line plot for number of deaths in China in March.</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Plot a bar graph of number of daily cases in USA?</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Draw a line chart of total cases in Wuhan since February.</b-dropdown-item-button>
                </b-dropdown-group>
            </transition>

            <transition name="with-mode-fade" mode="out-in">
                <b-dropdown-group v-if="cat_on" key="on" @click="traversCat('C', 'cat_on', 'subcat_3_on')" header="Recommendations" class="dd-options-parent dd-sm"></b-dropdown-group>

                <b-dropdown-group v-else-if="subcat_3_on" key="off" @click="traversCat('S', 'cat_on', 'subcat_3_on')" id="dropdown-group-3" header="< Back to Category" class="dd-options-parent">
                    <b-dropdown-divider></b-dropdown-divider>

                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Is it safe to go for a walk</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Can spraying alcohol or chlorine all over your body kill the new coronavirus?</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Is it safe to sit in an air-conditioned office</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Can eating chyavanprash help against coronavirus?</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Should I take H1N1 vaccine?</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">How long must I observe quarantine?</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Should I take a flu shot</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Can coronavirus be transmitted in areas with hot and humid climates?</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">Should I spray alcohol on my body</b-dropdown-item-button>
                </b-dropdown-group>
            </transition>

            <transition name="with-mode-fade" mode="out-in">
                <b-dropdown-group v-if="cat_on" key="on" @click="traversCat('C', 'cat_on', 'subcat_4_on')" header="Info" class="dd-options-parent dd-sm"></b-dropdown-group>

                <b-dropdown-group v-else-if="subcat_4_on" key="off" @click="traversCat('S', 'cat_on', 'subcat_4_on')" id="dropdown-group-4" header="< Back to Category" class="dd-options-parent">
                    <b-dropdown-divider></b-dropdown-divider>

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
            </transition>

            <transition name="with-mode-fade" mode="out-in">
                <b-dropdown-group v-if="cat_on" key="on" @click="traversCat('C', 'cat_on', 'subcat_5_on')" header="Procedures" class="dd-options-parent dd-sm"></b-dropdown-group>

                <b-dropdown-group v-else-if="subcat_5_on" key="off" @click="traversCat('S', 'cat_on', 'subcat_5_on')" id="dropdown-group-5" header="< Back to Category" class="dd-options-parent">
                    <b-dropdown-divider></b-dropdown-divider>

                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">How to disinfect my phone</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">How to disinfect my car</b-dropdown-item-button>
                    <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)">How to disinfect my room</b-dropdown-item-button>
                </b-dropdown-group>
            </transition>
        </b-dropdown>


        <!-- <b-dropdown-item-button class="dd-options" v-on:click="emitToTophead($event)"></b-dropdown-item-button> -->
    </div>
</template>

<style lang="sass">
.dd-options-parent
    cursor: pointer

.dd-sm header.dropdown-header:hover
    background-color: var(--dd-hoover-bg-color)

.m-2
    margin-left: 1.5rem !important

.sr-only
    margin-left: 21.5rem

#dropdown-grouped ul
    width: var(--overlay-dd-width) !important
    overflow-y: auto
    overflow-x: hidden

#dropdown-grouped button
    background-color: var(--header-btn-bg-color)

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

.with-mode-fade-enter-active, .with-mode-fade-leave-active
    transition: opacity .5s

.with-mode-fade-enter, .with-mode-fade-leave-active
    opacity: 0
</style>

<script>
export default {
    data(){
        return {
            querySelection: '',
            cat_on: true,
            subcat_1_on: false,
            subcat_2_on: false,
            subcat_3_on: false,
            subcat_4_on: false,
            subcat_5_on: false
        }
    },
    methods: {
        // Define the method that emits data to the parent as the first parameter to `$emit()`.
        // This is referenced in the <template> call in the parent. The second parameter is the payload.
        emitToTophead (event) {
            // alert(event.target.innerHTML);

            this.$emit('dropdownToTophead', event.target.innerHTML)
        },
        // This is for the category/subcategory traversal feature
        traversCat(cat_type, cat_var, sub_cat_var) {
            // alert(cat_type + " ---- " + cat_var + " ---- " + sub_cat_var);

            if(cat_type != "" && cat_var != "") {
                if(cat_type == "C") {
                    this[cat_var] = false; 
                    this[sub_cat_var] = true;
                } else  if(cat_type == "S") {
                    this[sub_cat_var] = false;
                    setTimeout(() => { 
                        this[cat_var] = true
                    }, 500)
                }
            }
        }
    }
}
</script>