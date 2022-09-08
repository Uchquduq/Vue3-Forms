<template>
  <div>
    <h1>Create an event</h1>
    <form @submit.prevent="post">
      <BaseSelect :options="categories" v-model="event.category" label="Select a category" />

      <h3>Name & describe your event</h3>
      <BaseInput v-model="event.title" label="Title" type="text" />
      <BaseInput v-model="event.desciption" label="Description" type="text" />

      <h3>Where is your event?</h3>
      <BaseInput v-model="event.location" label="Location" type="text" />

      <h3>Are pets allowed?</h3>
      <div>
        <BaseRadio v-model="event.pets" name="pets" :value="1" label="Yes" />
      </div>

      <div>
        <BaseRadio v-model="event.pets" name="pets" :value="0" label="No" />
      </div>

      <h3>Extras</h3>
      <div>
        <BaseCheckbox v-model="event.extras.catering" label="Catering" />
      </div>

      <div>
        <BaseCheckbox v-model="event.extras.music" label="Live Music" />
      </div>

      <button type="submit">Submit</button>
    </form>

    <pre>{{ event }}</pre>
  </div>
</template>

<script>
import BaseInput from '@/components/BaseInput';
import BaseSelect from '@/components/BaseSelect';
import BaseCheckbox from '@/components/BaseCheckbox';
import EventService from '@/services/EventService';
import BaseRadio from '@/components/BaseRadio.vue';
export default {
  data() {
    return {
      categories: [
        "sustainability",
        "nature",
        "animal welfare",
        "housing",
        "education",
        "food",
        "community"
      ],
      event: {
        category: "",
        title: "",
        description: "",
        location: "",
        pets: 1,
        extras: {
          catering: false,
          music: false
        }
      }
    };
  },
  components: { BaseInput, BaseSelect, BaseCheckbox, BaseRadio },
  methods: {
    post() {
      EventService.postEvent(this.event)
        .then((response) => (console.log(response.data)))
        .catch((error) => console.log(error));
    }
  }
}
</script>
