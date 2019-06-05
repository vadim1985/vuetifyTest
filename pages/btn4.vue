<template>
    <v-container>
        <v-layout row wrap>
            <v-flex xs12 sm10 md8 offset-sm1 offset-md2>
                <v-btn @click="showMsg" color="purple darken-1">show</v-btn>
                <h1>Button 4</h1>
            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
export default {
    methods:{
        showMsg(){
            let myVariable = {
                age: 23,
                name: 'Tom',
                weight: 140,
                heigth: 80,
                nik: 'Alien',
                x: 2,
                y: 3,
                f1 : function(){
                    console.log(this.x + this.y);
                },
                newObject:{
                    q:1,
                    w:2,
                    e:3
                }
            };

            let j = 0;
            for (const key in myVariable) {
                if (!(typeof myVariable[key] === 'object')){
                   console.log("Primitive - " + myVariable[key])
                }
                if(typeof myVariable[key] === 'function'){
                    console.log(" Function " + myVariable[key])
                }
            }
        }
    }
}
</script>