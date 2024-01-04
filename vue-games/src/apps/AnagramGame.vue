<template>
    <p>This is my Anagram Hunt</p>
    <div>
        <div>
            <label for="user-name">Username</label>
            <input name="user-name" id="user-name" v-model="userName">
        </div>
        <div>
            <label for="score">Score</label>
            <input type="number" name="score" id="score" v-model="score">
        </div>
        <div>
            <button @click="recordScore">Record Score</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'AnagramGame',
    data() {
        return {
            userName:'',
            score: 0
        }
    },
    methods: {
        async recordScore() {
            const data = {
                "user-name": this.userName,
                "score": this.score,
                "game": "ANAGRAM"
            };

            const response =(await this.axios.post("/record-score/", data)).data;

            console.log(response);
        }
    }
}
</script>

<style scoped>
    div, label {
        padding: 0.2rem;
    }
</style>
