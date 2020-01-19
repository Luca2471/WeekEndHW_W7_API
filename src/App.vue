<template lang="html">
  <body>
    <h1>NFL Teams By Number of Arrests</h1>
    <div>
      <teams-names-list :teamsNames="teamsNames"></teams-names-list>
      <div>
          <team-detail :selectedTeam="selectedTeam"></team-detail>
      </div>
    </div>
  </body>

</template>

<script>
import {eventBus} from './main.js';
import TeamsNamesList from './components/TeamsNamesList.vue';
import TeamDetail from './components/TeamDetail.vue'

export default {
  name: 'app',
  data(){
    return {
      teams: [],
      teamsNames: [],
      selectedTeam: null
    }
  },

  mounted(){
    fetch('http://nflarrest.com/api/v1/team')
      .then(result => result.json())
      .then(teams => {
        this.teamsNames = teams.map(team => team.Team_preffered_name)
        this.teams = teams
      })
      eventBus.$on('name-selected', (selectedTeamName) => {
        this.selectedTeam = this.getTeamByName(selectedTeamName)
      })
  },

  methos: {
    getTeamByname(teamName) {
      const foundTeam = this.teams.filter(team => team.Team_preffered_name === teamName)[1]
      return foundTeam
    }
  },

  components: {
    "teams-names-list": TeamsNamesList,
    "team-detail": TeamDetail
  }
}
</script>

<style lang="css" scoped>
</style>
