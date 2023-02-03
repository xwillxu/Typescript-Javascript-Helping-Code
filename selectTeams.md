### Below are a couple of examples that choose a team out of different amount of teams. Notice: You will need a team name for each team.

Below is the example for picking a team out of two teams.

```
selectTeam(teamOneScore, teamTwoScore, teamOne, teamTwo, teamOneName, teamTwoName) {
        let team = ""
        if (teamOneScore < teamTwoScore) {
            team = teamOneName
        } else if (teamTwoScore < teamOneScore) {
            team = teamTwoName
        } else if (teamOneScore == teamTwoScore) {
            const teamOnePlayers = teamOne.players
            const teamTwoPlayers = teamTwo.players
            if (teamOnePlayers < teamTwoPlayers) {
                team = teamOneName
            } else if (teamTwoPlayers < teamOnePlayers) {
                team = teamTwoName
            } else if (teamOnePlayers == teamTwoPlayers) {
                const randomNumber = random(1, 2)
                if (randomNumber == 1) {
                    team = teamOneName
                } else if (randomNumber == 2) {
                    team = teamTwoName
                }
            }
        }

     return team
}
```

Below is the example for picking a team out of a given number of teams.

```
selectTeam(amountOfTeams, teamObjects) {
        let newTeamName = ""
        const teams = []
        for (let x = 0; x < amountOfTeams; x++) {
            const team = {
                teamName: null,
                teamScore: null,
                teamPlayerAmount: 0,
            }

            team.teamName = teamObjects[x].name
            team.teamScore = teamObjects[x].score
            team.teamPlayerAmount = teamObjects[x].team.players

            teams.push(team)
        }
        
        
        let lowestScore = 0
        const equalScoreTeams = []

        for (const team of teams) {
            if (lowestScore > team.score) {
                lowestScore = team.score
                newTeamName = team.teamName
            }

            if (lowestScore == team.score) {
                equalScoreTeams.push(team)
            }
        }

```
