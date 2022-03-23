<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        click me
    </div>
</template>

<script>
export default {
    props: ["delay"],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    // lifecycle hooks functions
    //fires after the component has been mounted
    mounted() {
        console.log("component mounted");
        /* when the whole components mounts it will start the
        timeout & fire the function after the delay time meets */
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
            // to know how long we will wait
            console.log(this.delay);
        }, this.delay)
    },
    // fires when the data has been changed/updated, updated() hook fires
    updated() {
        console.log("component updated");
    },
    //fires after the component has been unmounted
    unmounted() {
        console.log("unmounted");
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },
        stopTimer() {
            clearInterval(this.timer)
            console.log(this.reactionTime);
        }

    }
}
</script>

<style>
.block {
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>