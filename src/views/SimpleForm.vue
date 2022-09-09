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
        <BaseRadioGroup v-model="event.pets" name="pets" :options="petOptions" vertical />
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
import BaseRadioGroup from '@/components/BaseRadioGroup.vue';
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
      },
      petOptions: [
        { label: 'Yes', value: 1 },
        { label: 'No', value: 0 }
      ]
    };
  },
  components: { BaseInput, BaseSelect, BaseCheckbox, BaseRadioGroup },
  methods: {
    post() {
      EventService.postEvent(this.event)
        .then((response) => (console.log(response.data)))
        .catch((error) => console.log(error));
    }
  }
}
</script>
