<template lang="html">
  <ul v-on="handleClick" v-model="selectedTeamName">
    <li v-for="teamName in teamsNames">{{teamName}}</li>

  </ul>
</template>

<script>
import{ eventBus } from '../main.js'

export default {
  name: 'teams-names-list',
  props: ['teamsNames'],

  data() {
    return {
      selectedTeamName: ""
    }
  },
  method: {
    handleClick(){
      eventBus.$emit('teams-names-list', this.selectedTeamName)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
