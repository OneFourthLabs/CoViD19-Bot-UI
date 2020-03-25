<template>
    <header class="app-head">
        <img v-if="app.avatarUri" class="app-icon" :alt="app.displayName" :src="app.avatarUri">
        <img v-else class="app-icon" src="https://console.dialogflow.com/api-client/assets/img/logo-short.png" :alt="app.displayName">
        <div class="app-info">
            <div class="app-name">{{app.displayName}}</div>
        </div>
        <slot />
        
        <!-- Suggestion dropdown -->
        <Dropdown class="suggestion-btn" v-on:dropdownToTophead="onDropdownClick" />

        <!-- Report dropdown -->
        <Dropdownform class="report-btn" />
    </header>

</template>

<style lang="sass" scoped>
@import '@/Style/Mixins'

.app-head
    z-index: 666
    padding: 12px
    position: fixed
    width: 100%

    @media screen and (max-width: 1000px)
        background-color: var(--background)

    .app-icon
        border-radius: 8px
        width: 30px
        height: 30px
        object-fit: cover
        background-color: var(--image-background)

    .app-info
        display: inline-block
        margin-left: 10px

        .app-name
            font-size: 18px
            font-weight: 500
            color: var(--text-logo)
            line-height: 15px

        .app-poweredby
            color: var(--text-secondary)
            font-size: 14px

            a[href]
                color: var(--text)
                text-decoration: none

.audio-toggle
    @include reset
    display: flex
    position: fixed
    top: 0
    right: 0
    margin: 8.5px 0
    z-index: 999
    padding: 8px
    background-color: var(--element-background)
    border-radius: 20px 0 0 20px
    cursor: pointer
    color: var(--text)
    transition: padding .25s ease

    &:hover
        padding-right: 20px

.suggestion-btn
    margin-left: var(--suggestion-btn-mrgn-left)
    margin-top: var(--suggestion-btn-mrgn-top)
    width: 120rem

.report-btn
    margin-left: var(--report-btn-mrgn-left)
    margin-top: var(--report-btn-mrgn-top)
</style>

<script>
import Dropdown from '@/Components/Rich/Dropdown.vue'
import Dropdownform from '@/Components/Rich/Dropdownform.vue'

export default {
    name: 'TopHead',
    data(){
        return {
            fromChild: ''
        }
    },
    components: {
        Dropdown,
        Dropdownform
    },
    methods: {
        // Triggered when `dropdownToTophead` event is emitted by the child.
        onDropdownClick (value) {
            // alert("In Tophead --> "+value);
            // this.fromChild = value
            this.$emit('topheadToApp', value)
        }
    },
    props: {
        app: {
            type: Object,
            default: null
        }
    }
}
</script>