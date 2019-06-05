<template>
<v-container>
    <v-layout row wrap>
        <v-flex>
            <v-btn @click="toZero">to zero</v-btn>
            <v-btn @click="fromValue">from value</v-btn>
        </v-flex>
        <v-flex>
            <h1>{{ biggerOrNot }}</h1>
        </v-flex>
    </v-layout>
</v-container>
</template>

<script>
export default {
    data(){
        return{
            dataToZero: 0,
            dataFromValue: 0
        }
    },
    computed:{
        biggerOrNot(){
            return this.dataToZero < this.dataFromValue ? "К нулю меньше" : "К значению меньше";
        }
    },
    methods:{
        toZero(){
            let max = 1000;
            let count = 0;
            var time = performance.now();
            for (let i = max; i > 0; i--) {
                count++;                
            }
            this.dataToZero = performance.now() - time;
            console.log("1 - " + count);
        },
        fromValue(){
            let max = 1000;
            let count = 0;
            var time = performance.now();
            for (let i = 0; i < max; i++) {
                count++;                
            }
            this.dataFromValue = performance.now() - time;
            console.log("2 - " + count);
        }
    }
}
</script>