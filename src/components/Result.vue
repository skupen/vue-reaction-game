<template>
    <div>
        <h2>{{ result }} ms</h2>
        <button @click="playAgainEmitter">Wanna fuck it up again?</button>
    </div>
</template>

<script>
export default {
    data(){
        return{
            isPlayAgainVisible: true
        }
    },
    props: ["result"],
    methods: {
        playAgainEmitter(){
            this.$emit("buttonAgain");
            this.isPlayAgainVisible = false;
        }
    }
}
</script>