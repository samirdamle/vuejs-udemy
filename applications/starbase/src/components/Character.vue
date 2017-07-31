<template>
    <div class="col-sm-4" @click="switchCharacter">
        <div class="character-card">
            <div class="card-block">
                <div class="card-title">
                    <h4>{{characterId}}. {{character.name}}</h4>
                </div>
                <p class="card-text">Height: {{character.height}}cm</p>
                <p class="card-text">Mass: {{character.mass}}kg</p>
                <p class="card-text">Hair Color: {{character.hair_color}}</p>
                <p class="card-text">Eye Color: {{character.eye_color}}</p>
                <p class="card-text">Birth Year: {{character.birth_year}}</p>
                <p class="card-text">Gender: {{character.gender}}</p>
            </div>
        </div>
        <br><br>
        {{character}}
    </div>
</template>
<script>
export default {
    props: [
        'id'
    ],
    data() {
        return {
            character: {

            },
            characterId: this.id
        }
    },
    methods: {
        fetchCharacter(id) {
            fetch(`http://swapi.co/api/people/${id}`, {
                method: 'GET'
            })
                .then(res => res.json())
                .then(character => {
                    this.character = character
                });
        },
        switchCharacter() {
            let randomId = Math.floor(Math.random() * 83) + 1
            this.characterId = randomId
            this.fetchCharacter(randomId)
        }
    },
    created() {
        this.fetchCharacter(this.id)
    }
}
</script>
<style lang="scss" scoped>

</style>
