<template>
    <div>
        <h2>{{ result }} ms</h2>
        <button @click="playAgainEmitter">Wanna fuck it up again?</button>
        <ul>
            <li v-for="sResult in aResults" :key="sResult">
                {{ sResult }}
            </li>
        </ul>
        <h3>average is {{ getAvg }} ms</h3>
    </div>
</template>

<script>
export default {
    data(){
        return{
            isPlayAgainVisible: true,
            avg: Number
        }
    },
    props: [
        "result",
        "aResults"
        ],
    methods: {
        playAgainEmitter(){
            this.$emit("buttonAgain");
            this.isPlayAgainVisible = false;
        }
    },
    computed: {
        getAvg(){
            let aResults = this.$props.aResults
            let avg = aResults.reduce(function (accumulator, currentValue) {
                    return accumulator + currentValue
                    }, 0)
            return Math.floor(avg/aResults.length);
        }
    }
}
</script>