<template>
    <v-container>
        <v-layout row wrap>
            <v-flex v-for="i in 5" :key="i" xs12 sm10 md8 offset-sm1 offset-md2>
                <v-alert :value="true" :type=getType @click="getcolor">
                    <h2>{{ i }} String</h2>
                </v-alert>
            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
export default {
    data(){
        return {
            t: null
        }
    },
    computed:{
        getType(){
            return this.t;
        }
 
    },
    methods:{
        getrnd(min, max){
            return Math.floor(Math.random() * (max - min)) + min;
        },
        getcolor(){
            switch(this.getrnd(1, 5)) {
            case 1:
                return this.t = 'success';
                break;
            case 2:
                return this.t = 'info';
                break;
            case 3:
                return this.t = 'warning';
                break;
            case 4:
                return this.t = 'error';
                break;
            }     
        }
    }
}
</script>


