<template>
  <div>
    <b-dropdown id="dropdown-form" text="Report" ref="dropdown" class="m-2">
      <b-dropdown-form class="dd-form">
        <b-form-group label="" label-for="dropdown-form-email">
          <b-form-input
            id="dropdown-form-email"
            size="sm"
            placeholder="Type your text"
            class="report-input"
          ></b-form-input>
            
        </b-form-group>
            
        <b-button variant="primary" size="sm" @click="onClick" class="report-sbmt-btn">Send</b-button>

      </b-dropdown-form>
    </b-dropdown>
  </div>
</template>

<style lang="sass">
.dd-form
    width: var(--dd-form-width)

#dropdown-form ul
    height: var(--dd-form-height)
    overflow: hidden

#dropdown-form button
    margin-left: 1rem

.report-input
    height: var(--report-input-height) 
    width: var(--report-input-width)

.report-sbmt-btn
    margin-top: var(--report-sbmt-mrgn-top)
    margin-left: var(--report-sbmt-mrgn-left) !important
    height: var(--report-sbmt-height)
    width: var(--report-sbmt-width)
</style>

<script>
  export default {
    methods: {
      onClick() {
        // Close the menu and (by passing true) return focus to the toggle button
        this.$refs.dropdown.hide(true)
      }
    }
  }
</script>