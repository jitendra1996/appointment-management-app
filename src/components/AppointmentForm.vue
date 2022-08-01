<template>
  <form
    @submit.prevent="formHandler"
    class="p-5 m-auto w-1/2 mt-5 rounded-lg overflow-hidden shadow-sm shadow-teal-500"
  >
    <legend class="text-2xl mb-5">Appointment</legend>
    <div class="w-full mb-5 text-center">
      <label for="detail" class="text-lg">Appointment details</label>
      <input
        type="text"
        v-model="details"
        id="details"
        class="border border-black p-1 w-1/2 ml-5"
      />
    </div>
    <div class="w-full mb-5 text-center">
      <label for="startDate" class="text-lg">Start Date</label>
      <input
        type="datetime-local"
        v-model="startDt"
        id="startDate"
        class="border border-black p-1 w-1/2 ml-5"
      />
    </div>
    <div class="w-full mb-5 text-center">
      <label for="endDate" class="text-lg">End Date</label>
      <input
        type="datetime-local"
        v-model="endDt"
        id="endDate"
        class="border border-black p-1 w-1/2 ml-5"
      />
    </div>
    <button
      type="submit"
      class="m-5 border-2 border-solid border-teal-500 text-lg px-5 py-2.5 rounded float-right bg-teal-500 text-white hover:border-2 hover:border-solid hover:border-teal-700 hover:shadow-inner hover:shadow-teal-700"
    >
      Fix Appointment
    </button>
  </form>

  <AppointmentTable :appointments="appointments"/>
</template>

<script>
import AppointmentTable from "@/components/AppointmentTable.vue";

export default {
  name: "AppointmentFrom",
  components: { AppointmentTable },
  data() {
    return {
      details: "",
      startDt: "",
      endDt: "",
      appointments: [],
    };
  },
  methods: {
    formHandler() {
      let obj = {
        details: this.details,
        startDt: new Date(this.startDt),
        endDt: new Date(this.endDt),
      };

      this.appointments.push(obj);
      this.appointments.sort((a, b) => a.startDt - b.startDt);
      // console.log(this.appointments);
      for (let i = 0; i < this.appointments.length - 1; i++) {
        if (
          this.appointments[i].startDt === this.appointments[i + 1].startDt ||
          this.appointments[i + 1].startDt < this.appointments[i].endDt
        ) {
          if (this.appointments[i].endDt > this.appointments[i + 1].endDt) {
            let ElIndex = i + 1;
            let count = 1;
            while (
              this.appointments[i].endDt !==
                this.appointments[ElIndex].startDt &&
              this.appointments[i].endDt > this.appointments[ElIndex].endDt
            ) {
              count++;
              ElIndex++;
            }
            this.appointments.splice(i+1, count);
          } else {
            this.appointments.shift();
          }
        }
      }
      // console.log(this.appointments);
    },
  },
};
</script>
