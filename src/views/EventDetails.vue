<template>
    <div v-if="event">
        <h1>{{ event.title }}</h1>
        <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
        <p>{{ event.decription }}</p>
    </div>

</template>

<script>

    import EventService from "@/services/EventService.js";

    export default {
        props: ['id'],
        data() {
            return {
                event: null
               
            }
        },
        created() {
            // fetch event by id and set the value of local data to it
             EventService.getEvent(this.id)
        .then(response => {
            console.log('event: ', response.data);
            this.event = response.data;
        })
        .catch(error => {
            console.log(error)
        })
        }
    }
</script>


<style>
</style>

