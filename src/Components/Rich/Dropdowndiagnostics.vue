<template>
  <div>
    <b-dropdown id="dropdown-form-diag" text="Diagnostics" ref="dropdown" class="m-2">
     <b-form @submit="onSubmit" v-if="show" class="dd-form-diag">

      <b-form-group id="form-input-age" label="" label-for="input-age" description="">
        <b-form-input
          id="input-age"
          v-model="form.age"
          type="number"
          min="0"
          max="150"
          required
          placeholder="Enter your age"
          class="diag-input"
          @input="getNow"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="form-input-diag_gender" label="Please select your gender" label-for="input-diag_gender" class="diag-input">
        <b-form-radio v-model="form.gender" name="diag_gender-radios" value="Male">Male</b-form-radio>
        <b-form-radio v-model="form.gender" name="diag_gender-radios" value="Female">Female</b-form-radio>
        <b-form-radio v-model="form.gender" name="diag_gender-radios" value="Others">Others</b-form-radio>
      </b-form-group>

      <b-form-group id="form-input-diag_bodytemp" label="Please let us know your current body temperature in degree Fahrenheit (Normal body temperature is 98.6°F):" label-for="input-diag_bodytemp" class="diag-input" style="margin-top: 4.5rem !important;">
        <b-form-radio v-model="form.bodytemp" name="diag_bodytemp-radios" value="Normal (96°F-98.6°F)">Normal (96°F-98.6°F)</b-form-radio>
        <b-form-radio v-model="form.bodytemp" name="diag_bodytemp-radios" value="Fever (98.6°F-102°F)">Fever (98.6°F-102°F)</b-form-radio>
        <b-form-radio v-model="form.bodytemp" name="diag_bodytemp-radios" value="High Fever (>102°F)">High Fever (>102°F)</b-form-radio>
        <b-form-radio v-model="form.bodytemp" name="diag_bodytemp-radios" value="none">Don't Know</b-form-radio>
      </b-form-group>

      <b-form-group label="Are you experiencing any of the symptoms below (mark all those applicable)" class="diag-input" style="margin-top: 9rem !important;">
        <b-form-checkbox-group
          v-model="form.symptoms"
          :options="symptoms_options"
          name="diag_symptoms"
          stacked
        ></b-form-checkbox-group>
      </b-form-group>
    
      <b-form-group label="Additionally, please verify if you are experiencing any of the symptoms below (mark all those applicable)" class="diag-input" style="margin-top: 10rem !important;">
        <b-form-checkbox-group
          v-model="form.additionalsymptoms"
          :options="additionalsymptoms_options"
          name="diag_additionalsymptoms"
          stacked
        ></b-form-checkbox-group>
      </b-form-group>

      <b-form-group id="form-input-diag_travelhistory" label="Please select your travel and exposure details" label-for="input-diag_travelhistory" class="diag-input" style="margin-top: 14rem !important;">
        <b-form-radio v-model="form.travelhistory" name="diag_travelhistory-radios" value="No Travel History">No Travel History</b-form-radio>
        <b-form-radio v-model="form.travelhistory" name="diag_travelhistory-radios" value="No contact with anyone with Symptom">No contact with anyone with Symptoms</b-form-radio>
        <b-form-radio v-model="form.travelhistory" name="diag_travelhistory-radios" value="History of travel or meeting in affected geographical area in last 14 day">History of travel or meeting in affected geographical area in last 14 days</b-form-radio>
        <b-form-radio v-model="form.travelhistory" name="diag_travelhistory-radios" value="Close Contact with confirmed COVID in last 14 days">Close Contact with confirmed COVID in last 14 days</b-form-radio>
      </b-form-group>

      <b-form-group label="Do you have a history of any of these conditions (mark all those applicable)" class="diag-input" style="margin-top: 13.5rem !important;">
        <b-form-checkbox-group
          v-model="form.conditions"
          :options="conditions_options"
          name="diag_conditions"
          stacked
        ></b-form-checkbox-group>
      </b-form-group>

      <b-form-group id="form-input-diag_symptomprogression" label="How have your symptoms progressed over the last 48 hrs?" label-for="input-diag_symptomprogression" class="diag-input" style="margin-top: 12rem !important;">
        <b-form-radio v-model="form.symptomprogression" name="diag_symptomprogression-radios" value="No Change">No Change</b-form-radio>
        <b-form-radio v-model="form.symptomprogression" name="diag_symptomprogression-radios" value="Improved">Improved</b-form-radio>
        <b-form-radio v-model="form.symptomprogression" name="diag_symptomprogression-radios" value="Worsened">Worsened</b-form-radio>
        <b-form-radio v-model="form.symptomprogression" name="diag_symptomprogression-radios" value="Worsened Considerably">Worsened Considerably</b-form-radio>
      </b-form-group>

      <b-form-group id="form-datetime" label="" label-for="input-datetime" style="display:none;margin-top: 12rem !important;">
        <b-form-input
          id="input-datetime"
          v-model="form.datetime"
          placeholder="Enter date time"
          class="report-input"
        ></b-form-input>
      </b-form-group>

      <b-button type="submit" id="submit_loader_diag" variant="primary" class="diag-sbmt-btn">Submit</b-button>
      
      <!-- Loader button -->
      <b-button class="diag-sbmt-btn" variant="primary" disabled id="loader_diag" style="display:none">
        <b-spinner small type="grow"></b-spinner>
        Submitting...
      </b-button>

    </b-form>
    </b-dropdown>
  </div>
</template>

<style lang="sass">
.dd-form-diag
    width: var(--dd-form-diag-width) !important

#dropdown-form-diag ul
    height: var(--dd-form-diag-height) !important
    overflow: auto
    margin-left: var(--dd-form-diag-mrgn-left)

#dropdown-form-diag button
    margin-left: 1rem

.diag-input
    height: var(--diag-input-height) 
    width: var(--diag-input-width)
    margin-top: var(--diag-input-mrgn-top)
    margin-left: var(--diag-input-mrgn-left)
    color: var(--text-subtitle)

.diag-sbmt-btn
    margin-top: var(--diag-sbmt-mrgn-top)
    margin-left: var(--diag-sbmt-mrgn-left) !important
    height: var(--diag-sbmt-height)
    width: var(--diag-sbmt-width)
</style>

<script>
export default {
  data() {
    return {
      form: {
        age: '',
        gender: 'Male',
        bodytemp: 'Normal (96°F-98.6°F)',
        symptoms: [],
        additionalsymptoms: [],
        travelhistory: 'No Travel History',
        conditions: [],
        symptomprogression: 'No Change',
        datetime: ''
      },
      symptoms_options: [
        { text: 'Dry Cough', value: 'Dry Cough' },
        { text: 'Loss or diminished sense of smell', value: 'Loss or diminished sense of smell' },
        { text: 'Sore Throat', value: 'Sore Throat' },
        { text: 'Weakness', value: 'Weakness' },
        { text: 'Change in Appetite', value: 'Change in Appetite' }
      ],
      additionalsymptoms_options: [
        { text: 'Moderate to Severe Cough', value: 'Moderate to Severe Cough' },
        { text: 'Feeling Breathless', value: 'Feeling Breathless' },
        { text: 'Difficulty in Breathing', value: 'Difficulty in Breathing' },
        { text: 'Drowsiness', value: 'Drowsiness' },
        { text: 'Persistant Pain and Pressure in Chest', value: 'Persistant Pain and Pressure in Chest' },
        { text: 'Severe Weakness', value: 'Severe Weakness' }
      ],
      conditions_options: [
        { text: 'Diabetes', value: 'Diabetes' },
        { text: 'High Blood Pressure', value: 'High Blood Pressure' },
        { text: 'Heart Disease', value: 'Heart Disease' },
        { text: 'Kidney Disease', value: 'Kidney Disease' },
        { text: 'Lung disease', value: 'Lung disease' },
        { text: 'Stroke', value: 'Stroke' },
        { text: 'Reduced Immunity', value: 'Reduced Immunity' }
      ],
      show: true
    }
  },
  methods: {
    onSubmit(evt) {
      evt.preventDefault()
        // Loader
        document.getElementById("submit_loader_help").style.display = "none";
        document.getElementById("loader_help").style.display = "";

        console.log(JSON.stringify(this.form))
        return false

        let dataEndPoint = 'https://db-server-dot-corona-bot-gbakse.appspot.com/post_help';

        this.$http.post ( dataEndPoint, JSON.stringify(this.form) ).then(function () {
          return false

          let emitText = "I have submitted by diagnostic enquiry form with id #xxxx#. Please let me know the details";

          this.onClick()
          this.onReset(evt)
          this.$emit('dropdowndiagToTophead', emitText)
        });
    },
    onClick() {
      // Close the menu and (by passing true) return focus to the toggle button
      this.$refs.dropdown.hide(true)
    },
    onReset(evt) {
      evt.preventDefault()
      // Reset our form values
      this.form.age = ''
      this.form.gender = 'Male'
      this.form.bodytemp = 'TNormal (96°F-98.6°F)'
      this.form.symptoms = []
      this.form.additionalsymptoms = []
      this.form.travelhistory = 'No Travel History'
      this.form.conditions = []
      this.form.symptomprogression = 'No Change'
      this.form.datetime = this.getNow()

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