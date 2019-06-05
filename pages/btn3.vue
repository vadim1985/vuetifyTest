<template>
    <v-container>
        <v-layout row wrap>
            <v-flex xs12 sm10 md8 offset-sm1 offset-md2>
                    <v-progress-linear height="20" v-model="progressWidth"></v-progress-linear>
            </v-flex>
            <v-flex xs12 sm10 md8 offset-sm1 offset-md2 v-for="(item, index) in info" :key="index">
                <label v-if="!controls[index].activated">{{ item.name }}</label>
                <v-badge :color="controls[index].error ? 'red': 'green'" v-if="controls[index].activated">
                <template v-slot:badge v-if="controls[index].error">
                    <span>!</span>
                </template>
                <template v-slot:badge v-else>
                    <v-icon dark small>
                    done
                    </v-icon>
                </template>
                <label>{{ item.name }}</label>
                </v-badge>
                <v-text-field :value="item.value" @input="onInput(index, $event)"></v-text-field>
            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
export default {
    data(){
        return{
            info: [
					{
						name: 'Name',
						value: '',
						pattern: /^[a-zA-Z ]{2,30}$/
					},
					{
						name: 'Phone',
						value: '',
						pattern: /^[0-9]{7,14}$/
					},
					{
						name: 'Email',
						value: '',
						pattern: /.+/
					},
					{
						name: 'Some Field 1',
						value: '',
						pattern: /.+/
					},
					{
						name: 'Some Field 2',
						value: '',
						pattern: /.+/
					}
                ],
                controls: []
        }
    },
    created(){
        for(let i = 0; i < this.info.length; i++){
            this.controls.push({
                error: !this.info[i].pattern.test(this.info[i].value),
                activated: this.info[i].value != ''
            });
        }
    },
    methods: {
        onInput(index, value){
            let data = this.info[index];
            let control = this.controls[index];

            data.value = value;
            control.error = !data.pattern.test(value);
            control.activated = true;
        }
    },
    computed: {
        done(){
            let done = 0;

            for(let i = 0; i < this.controls.length; i++){
                if(!this.controls[i].error){
                    done++;
                }
            }

            return done;
        },
        progressWidth(){
            return (this.done / this.info.length * 100)
        }
    }
}
</script>