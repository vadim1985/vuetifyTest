<template>
    <v-container>
        <v-layout>
            <v-flex v-for="(item, index) in newArr" :key="index">
                <v-chip
                    v-model="item[index]"
                    close
                    @input="delObj(item)"
                    >
                    {{ item }}
                </v-chip>
            </v-flex>
            <v-container>
                <v-layout column>
                    <v-flex>
                        <v-btn @click="iteration">GoGoGo</v-btn>
                        <v-btn @click="addToObj">YesYesYes</v-btn>
                    </v-flex>
                </v-layout>
            </v-container>
        </v-layout>
    </v-container>
</template>

<script>
export default {
    data(){
        return{
            objArr: {
                "a": "a1",
                "b": "b2",
                "c": "c3"
            },
            newArr: []
        }
    },
    methods:{
        iteration(){
            for (const key in this.objArr) {
                if (this.objArr.hasOwnProperty(key)) {
                    console.log(key + " " + this.objArr[key]);
                    this.newArr.push({[key]: this.objArr[key]});                 
                }
            }
            console.log(this.newArr)
        },
        delObj(item){
            console.log(this.newArr.indexOf(item))
           this.newArr.slice(this.newArr.indexOf(item), 1)
        },
        addToObj(){
            let arr = this.newArr;
            var result = arr.reduce(function(obj,item){
                console.log(item.key + " - " + item.value)
                obj[item.key] = item.value; 
                return obj;
            }, {});
            console.log(result)
        }
    }
}
</script>
