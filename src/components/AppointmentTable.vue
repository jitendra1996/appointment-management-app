<template>
  <table class="m-auto mt-10 text-center">
    <thead class="border-teal-500 border-b bg-teal-600 text-white">
        <th class="px-10 py-2">S.No.</th>
        <th class="px-10 py-2">fixed Appointments</th>
        <th class="px-10 py-2">start date and time</th>
        <th class="px-10 py-2">end date and time</th>
    </thead>
    <tbody>
        <tr v-for="appointment,index in appointments" :key="index" class="border-teal-500 border-b hover:bg-slate-600 hover:text-white">
            <td class="px-10 py-2">{{ index+1 }}</td>
            <td class="px-10 py-2">{{appointment.details}}</td>
            <td class="px-10 py-2">{{appointment.startDt}}</td>
            <td class="px-10 py-2">{{appointment.endDt}}</td>
        </tr>
    </tbody>
  </table>
</template>

<script>
export default {
    props:["appointments"],
    name : "AppointmentTable",
}
</script>

<style>

</style>