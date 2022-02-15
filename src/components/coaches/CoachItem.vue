<template>
  <li>
    <h3>{{ fullName }}</h3>
    <h4>${{ rate }}/hour</h4>
    <div>
      <base-badge
        v-for="area in areas"
        v-bind:key="area"
        v-bind:type="area"
        v-bind:class="area"
        v-bind:title="area"
      ></base-badge>
    </div>
    <div class="actions">
      <base-button mode="outline" link="true" v-bind:to="coachContactLink"
        >Contact</base-button
      >
      <base-button link="true" v-bind:to="coachDetailsLink"
        >View Details</base-button
      >
    </div>
  </li>
</template>

<script>
import BaseButton from '../ui/BaseButton.vue';
export default {
  components: { BaseButton },
  props: ['id', 'firstName', 'lastName', 'rate', 'areas'],
  computed: {
    fullName() {
      return this.firstName + ' ' + this.lastName;
    },
    coachContactLink() {
      return this.$route.path + '/' + '/contact'; // /coaches/c1/contact
    },
    coachDetailsLink() {
      return '/coaches/' + this.id;
    },
  },
};
</script>

<style scoped>
li {
  margin: 1rem 0;
  border: 1px solid #424242;
  border-radius: 12px;
  padding: 1rem;
}

h3 {
  font-size: 1.5rem;
}

h3,
h4 {
  margin: 0.5rem 0;
}

div {
  margin: 0.5rem 0;
}

.actions {
  display: flex;
  justify-content: flex-end;
}
</style>
