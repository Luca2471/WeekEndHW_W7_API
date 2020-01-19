<template lang="html">
  <div v-if="selectedTeam">
    <h4>{{selectedTeam.Team_preffered_name}}</h4>
    <p>{{ selectedTeam.arrest_count}}</p>
    <p>{{  selectedTeam.Team_city}}</p>
    <p>{{ selectedTeam.Team_Conference_Division }}</p>
  </div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
  name:'team-detail',
  props: ['selectedTeam'],
}
</script>

<style lang="css" scoped>
</style>
