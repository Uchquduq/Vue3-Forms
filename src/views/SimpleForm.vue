<template>
  <div>
    <h1>Create an Event</h1>
    <form action="">
      <label for="">Select an category</label>
      <select name="" id="" v-model="event.category">
        <option v-for="option in categories" :key="option" :value="option" :selected="option === event.category">
          {{ option }}
        </option>
      </select>
      <h3>Name & describe your @leave=""</h3>
      <label for="">Title</label>
      <input type="text" v-model="event.title" class="field" placeholder="Title">

      <label for="">Description</label>
      <input type="text" v-model="event.description" placeholder="Description" class="field">

      <h3>Where is your event?</h3>
      <label for="">Location</label>
      <input type="text" v-model="event.location" placeholder="Location" class="field">

      <h3>Are pets allowed?</h3>
      <div>
        <input type="radio" v-model="event.pets" :value="1" name="pets">
        <label for="">Yes</label>
      </div>
      <div>
        <input type="radio" v-model="event.pets" :value="0" name="pets">
        <label for="">No</label>
      </div>

      <h3>Extras</h3>
      <div>
        <input type="checkbox" v-model="event.extras.catering" class="field" name="pets">
        <label for="">Catering</label>
      </div>
      <div>
        <input type="checkbox" v-model="event.extras.music" class="field" name="pets">
        <label for="">Live music</label>
      </div>
      <button class="button -fill-gradient" type="submit">Submit</button>
    </form>
  </div>
</template>

<script>

export default {
  name: "SimpleForm",
  data: () => ({
    categories: [
      'sustainability',
      'nature',
      'animal welfare',
      'hausing',
      'education',
      'food',
      'community'
    ],
    event: {
      category: '',
      title: '',
      description: '',
      location: '',
      pets: 1,
      extras: {
        catering: false,
        music: false
      }
    }
  })
};
</script>
