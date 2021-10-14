<template>
  <div class="subPage white">
    <SubPageBanner />
    <Calendar /> 
    <CalendarUpcomingEvents />
  </div>
</template>

<script>
    import SubPageBanner from '../../components/SubPageBanner.vue' 
    import Calendar from '../../components/Calendar.vue' 
    import CalendarUpcomingEvents from '../../components/CalendarUpcomingEvents.vue'

    export default {
        data: () => ({
            
        }),
    }

</script>

