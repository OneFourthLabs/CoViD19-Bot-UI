<template>
  <div>
    <b-dropdown id="dropdown-form" text="Report" ref="dropdown" class="m-2">
     <b-form @submit="onSubmit" v-if="show" class="dd-form">

      <b-form-group id="form-input-name" label="" label-for="input-name">
        <b-form-input
          id="input-name"
          v-model="form.name"
          required
          placeholder="Enter name"
          class="report-input"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="form-input-phone" label="" label-for="input-phone" description="">
        <b-form-input
          id="input-phone"
          v-model="form.phone"
          type="number"
          max-length="12"
          required
          placeholder="Enter phone number"
          class="report-input"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="form-input-email" label="" label-for="input-email" description="">
        <b-form-input
          id="input-email"
          v-model="form.email"
          type="email"
          placeholder="Enter email (optional)"
          class="report-input"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="form-input-report_category" label="" label-for="input-report_category">
        <b-form-select
          id="input-report_category"
          v-model="form.report_category"
          :options="report_categories"
          class="report-input"
          required
        ></b-form-select>
      </b-form-group>

      <b-form-group id="form-input-report_message" label="" label-for="input-report_message" description="">
        <b-form-textarea
          id="input-report_message"
          v-model="form.report_message"
          type="text"
          placeholder="Enter your message (optional)"
          class="report-input"
        ></b-form-textarea>
      </b-form-group>

      <b-form-group id="form-input-check">
        <b-form-checkbox-group v-model="form.checked" id="checkboxes-location" @input="getLocation">
          <b-form-checkbox value="share_location" class="report-input" required>Agree to share location</b-form-checkbox>
        </b-form-checkbox-group>
      </b-form-group>

      <b-form-group id="form-input-latlong" label="" label-for="input-latlong" style="display:none;">
        <b-form-input
          id="input-lat"
          v-model="form.lat"
          placeholder="Enter latitude"
          class="report-input"
        ></b-form-input>

        <b-form-input
          id="input-long"
          v-model="form.long"
          placeholder="Enter longitude"
          class="report-input"
        ></b-form-input>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
    </b-form>
    </b-dropdown>
  </div>
</template>

<style lang="sass">
.dd-form
    width: var(--dd-form-width)

#dropdown-form ul
    height: var(--dd-form-height)
    overflow: auto

#dropdown-form button
    margin-left: 1rem

.report-input
    height: var(--report-input-height) 
    width: var(--report-input-width)
    margin-top: var(--report-input-mrgn-top)
    margin-left: var(--report-input-mrgn-left)

.report-sbmt-btn
    margin-top: var(--report-sbmt-mrgn-top)
    margin-left: var(--report-sbmt-mrgn-left) !important
    height: var(--report-sbmt-height)
    width: var(--report-sbmt-width)
</style>

<script>
export default {
  data() {
    return {
      form: {
        name: '',
        phone: '',
        email: '',
        report_category: null,
        checked: [],
        lat: '',
        long: ''
      },
      // report_categories: [{ text: 'Select reporting category', value: null }, 'Carrots', 'Beans', 'Tomatoes', 'Corn'],
      report_categories: [
        { value: null, text: 'Select reporting category' },
        {
          label: 'Household items',
          options: [
            { value: { Household_items: 'Vegetables' }, text: 'Vegetables' },
            { value: { Household_items: 'Drinking Water'}, text: 'Drinking Water' },
            { value: { Household_items: 'Milk'}, text: 'Milk' },
            { value: { Household_items: 'Atta'}, text: 'Atta' },
            { value: { Household_items: 'Rice'}, text: 'Rice' },
            { value: { Household_items: 'Other grocery items' }, text: 'Other grocery items' },
            { value: { Household_items: 'Toiletries' }, text: 'Toiletries' }
          ]
        },
        {
          label: 'Medical supplies',
          options: [
            { value: { Medical_supplies: 'Masks' }, text: 'Masks' },
            { value: { Medical_supplies: 'Gloves' }, text: 'Gloves' },
            { value: { Medical_supplies: 'Sanitisers' }, text: 'Sanitisers' }
          ]
        },
        {
          label: 'Violations',
          options: [
            { value: { Violations: 'Hoarding' }, text: 'Hoarding' },
            { value: { Violations: 'Violating Social distancing' }, text: 'Violating Social distancing ' },
            { value: { Violations: 'Violating Curfew' }, text: 'Violating Curfew' },
            { value: { Violations: 'Violating' }, text: 'Violating ' }
          ]
        },
        {
          label: 'Emergencies',
          options: [
            { value: { Emergencies: 'I have symptoms of corona' }, text: 'I have symptoms of corona' },
            { value: { Emergencies: 'I need to see a doctor' }, text: 'I need to see a doctor' },
            { value: { Emergencies: 'I need an ambulance' }, text: 'I need an ambulance' }
          ]
        }
      ],
      show: true
    }
  },
  methods: {
    onSubmit(evt) {
      evt.preventDefault()
      if(this.form.checked == "share_location") {
        console.log(JSON.stringify(this.form))
        this.$http.post ( 'http://34.66.213.160/post_report', JSON.stringify(this.form) ).then(function () {
          this.onClick()
          this.onReset(evt)
        });
      } else {
        alert("Pleae click the checkbox and agree to share location details")
        return false
      }
    },
    onClick() {
      // Close the menu and (by passing true) return focus to the toggle button
      this.$refs.dropdown.hide(true)
    },
    getLocation(evt) {
      if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(this.showPosition)
      } else { 
        alert("Geolocation is not supported by this browser.")
      }
    },
    showPosition(position) {
      if(this.form.checked == "share_location") {
        // alert("Latitude: " + position.coords.latitude + " ------- Longitude: " + position.coords.longitude)
        this.form.lat = position.coords.latitude
        this.form.long = position.coords.longitude
      } else {
        this.form.lat = ''
        this.form.long = ''
      }
    },
    onReset(evt) {
      evt.preventDefault()
      // Reset our form values
      this.form.name = ''
      this.form.phone = ''
      this.form.email = ''
      this.form.lat = ''
      this.form.long = ''
      this.form.report_category = null
      this.form.checked = []
      // Trick to reset/clear native browser form validation state
      this.show = false
      this.$nextTick(() => {
        this.show = true
      })
    }
  }
}
</script>