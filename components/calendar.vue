<template>
<div class="col-lg-12 control-section">
    <div id="control_wrapper" class="col-lg-6 col-sm-8 col-md-8 multiselectWrapper">
        <div id="container" style="overflow:auto">
              <ejs-calendar :values="date"  ref="calendarInstance" :isMultiSelection="multiSelection" :created="onValueChange" :change="onValueChange"></ejs-calendar>
        </div>         
    </div>
    <div class="valuesWrapper col-lg-6 col-sm-8 col-md-8">
      <h5>Selected values</h5>
      <div class="contentValue">
        <div id="multiSelect">
        </div>
    </div>
    </div>
</div>
</template>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
</style>

<script>
import Vue from "vue";
import { CalendarPlugin } from "@syncfusion/ej2-vue-calendars";

Vue.use(CalendarPlugin);
export default Vue.extend({
  data: function() {
    let year = new Date().getFullYear();
    let month = new Date().getMonth();
    return {
      multiSelection: true,
      date: [
        new Date(year, month, 10),
        new Date(year, month, 15),
        new Date(year, month, 25)
      ]
    };
  },
  methods: {
    onValueChange: function() {
      let element = document.getElementById("multiSelect");
      element.innerHTML = "";
      for (let index = 0; index < this.$refs.calendarInstance.values.length; index++) {
        element.insertBefore(document.createTextNode(this.$refs.calendarInstance.values[index].toString()), element.children[0]);
        element.insertBefore(document.createElement('br'), element.childNodes[0]);
      }
    }
  }
});
</script>

<style>
#control_wrapper {
  max-width: 330px;
  margin: 0 auto;
}
#control_wrapper.multiselectWrapper{
    float: none;
}
.contentValue {
   padding: 10px;
    overflow: auto;
    max-height: 100px;
    margin-bottom: 10px;
    border: 1px solid rgba(0, 0, 0, 0.12);
}

.e-bigger #wrapper,
.e-bigger#wrapper {
        max-width: 300px;
}

.valuesWrapper {
    margin: 0 auto;
    float: none;
    padding: 0;
    max-width: 370px;

}

body.highcontrast .contentValue {
  border: 1px solid #969696;
}
</style>