<template>
  <div>
    <b-dropdown id="dropdown-form" text="Need Help/Volunteer" ref="dropdown" class="m-2">
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

      <b-form-group id="form-input-help_type" label="" label-for="input-help_type" class="report-input">
        <b-form-radio v-model="form.help_type" name="help_type-radios" value="help">I Need Help</b-form-radio>
        <b-form-radio v-model="form.help_type" name="help_type-radios" value="volunteer">I Want to Help</b-form-radio>
      </b-form-group>

      <b-form-group id="form-input-help_category" label="" label-for="input-help_category">
        <b-form-select
          id="input-help_category"
          v-model="form.help_category"
          :options="help_categories"
          class="report-input"
          required
        ></b-form-select>
      </b-form-group>

      <b-form-group id="form-input-help_message" label="" label-for="input-help_message" description="">
        <b-form-textarea
          id="input-help_message"
          v-model="form.help_message"
          type="text"
          placeholder="Enter your message (optional)"
          class="report-input"
        ></b-form-textarea>
      </b-form-group>

      <b-form-group id="form-input-check">
        <b-form-checkbox-group v-model="form.checked" id="checkboxes-location">
          <b-form-checkbox value="share_location" class="report-input" @input="getLocation" required>Agree to share location</b-form-checkbox>
          <b-form-checkbox value="share_contact" class="report-input" required>Agree to share contact information</b-form-checkbox>
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

        <b-form-input
          id="input-datetime"
          v-model="form.datetime"
          placeholder="Enter date time"
          class="report-input"
        ></b-form-input>
      </b-form-group>

      <b-button type="submit" id="submit_loader" variant="primary" class="report-sbmt-btn">Submit</b-button>
      
      <!-- Loader button -->
      <!-- <b-button variant="primary" id="loader" style="display:none1;">
        <b-spinner small type="grow"></b-spinner>
        Loading...
      </b-button> -->

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
    color: var(--text-subtitle)

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
        help_message: '',
        help_category: null,
        checked: [],
        lat: '',
        long: '',
        datetime: '',
        help_type: 'help'
      },
      help_categories: [
        { value: null, text: 'Select help category' },
        {
          label: 'Household items',
          options: [
            { value: { "main": 'Household items', "sub": 'Vegetables' }, text: 'Vegetables' },
            { value: { "main": 'Household items', "sub": 'Drinking Water'}, text: 'Drinking Water' },
            { value: { "main": 'Household items', "sub": 'Milk'}, text: 'Milk' },
            { value: { "main": 'Household items', "sub": 'Atta'}, text: 'Atta' },
            { value: { "main": 'Household items', "sub": 'Rice'}, text: 'Rice' },
            { value: { "main": 'Household items', "sub": 'Other grocery items' }, text: 'Other grocery items' },
            { value: { "main": 'Household items', "sub": 'Toiletries' }, text: 'Toiletries' }
          ]
        },
        {
          label: 'Medical supplies',
          options: [
            { value: { "main": 'Medical supplies', "sub": 'Masks' }, text: 'Masks' },
            { value: { "main": 'Medical supplies', "sub": 'Gloves' }, text: 'Gloves' },
            { value: { "main": 'Medical supplies', "sub": 'Sanitisers' }, text: 'Sanitisers' }
          ]
        },
        {
          label: 'Violations',
          options: [
            { value: { "main": 'Violations', "sub": 'Hoarding' }, text: 'Hoarding' },
            { value: { "main": 'Violations', "sub": 'Violating Social distancing' }, text: 'Violating Social distancing ' },
            { value: { "main": 'Violations', "sub": 'Violating Curfew' }, text: 'Violating Curfew' },
            { value: { "main": 'Violations', "sub": 'Violating' }, text: 'Violating ' }
          ]
        },
        {
          label: 'Emergencies',
          options: [
            { value: { "main": 'Emergencies', "sub": 'I have symptoms of corona' }, text: 'I have symptoms of corona' },
            { value: { "main": 'Emergencies', "sub": 'I need to see a doctor' }, text: 'I need to see a doctor' },
            { value: { "main": 'Emergencies', "sub": 'I need an ambulance' }, text: 'I need an ambulance' }
          ]
        }
      ],
      show: true
    }
  },
  methods: {
    onSubmit(evt) {
      evt.preventDefault()

      if(this.form.checked.indexOf("share_location") > -1 && this.form.checked.indexOf("share_contact") > -1) {
        // console.log(JSON.stringify(this.form))

        let emitText = "Submit my request for help";
        if(this.form.help_type == "volunteer") {
          emitText = "Submit my request to help";
        }

        // alert("hi");
        // Loader enable
        // document.getElementById('submit_loader').style.display = 'none';

        this.$http.post ( 'https://972d1a69.ngrok.io/post_volunteer', JSON.stringify(this.form) ).then(function () {
          this.onClick()
          this.onReset(evt)
          this.$emit('dropdownformhelpToTophead', emitText)
        });
      } else if(this.form.checked.indexOf("share_location") == -1) {
        alert("Pleae click the checkbox and agree to share location details")
        return false
      } else if(this.form.checked.indexOf("share_contact") == -1) {
        alert("Pleae click the checkbox and agree to share contact details")
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
      if(this.form.checked.indexOf("share_location") > -1) {
        // alert("Latitude: " + position.coords.latitude + " ------- Longitude: " + position.coords.longitude)
        this.form.lat = position.coords.latitude
        this.form.long = position.coords.longitude
      } else {
        this.form.lat = ''
        this.form.long = ''
      }

      this.getNow()
    },
    onReset(evt) {
      evt.preventDefault()
      // Reset our form values
      this.form.name = ''
      this.form.phone = ''
      this.form.email = ''
      this.form.lat = ''
      this.form.long = ''
      this.form.datetime = ''
      this.form.help_category = null
      this.form.help_message = ''
      this.form.help_type = 'help'
      this.form.checked = []
      // Trick to reset/clear native browser form validation state
      this.show = false
      this.$nextTick(() => {
        this.show = true
      })
    },
    getNow() {
      const today = new Date();
      const date = today.getFullYear()+'-'+(today.getMonth()+1)+'-'+today.getDate();
      const time = today.getHours() + ":" + today.getMinutes() + ":" + today.getSeconds();
      const dateTime = date +' '+ time;
      this.form.datetime = dateTime;
    }
  }
}
</script>