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
        
        let leastPlayers = 21
        const equalAmountPlayersTeams = []

        if (equalScoreTeams.length > 1) {
            for (const team of equalScoreTeams) {
                if (leastPlayers > team.teamPlayerAmount) {
                    leastPlayers = team.teamPlayerAmount
                    newTeamName = team.teamName
                }

                if (leastPlayers == team.teamPlayerAmount) {
                    equalAmountPlayersTeams.push(team)
                }

            }
        }

        if (equalAmountPlayersTeams.length > 1) {
            newTeamName = equalAmountPlayersTeams[random(0, equalAmountPlayersTeams.length - 1)].teamName
        }


        return newTeamName
    }

```

Example code is below:
```
const blueTeam = this.teams.blue
        const redTeam = this.teams.red
        const blueTeamScore = blueTeam.score + (blueTeam.kills * 10)
        const redTeamScore = redTeam.score + (redTeam.kills * 10)

        const team = this.selectTeam(2, [
            {
                name: "blue",
                score: blueTeamScore,
                team: blueTeam
            },

            {
                name: "red",
                score: redTeamScore,
                team: redTeam
            }
        ])
```
