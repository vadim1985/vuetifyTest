<template>
    <v-container grid-list-sm>
        <v-layout row wrap>
            <v-flex xs12 sm10 md8 offset-sm1 offset-md2>
                <v-container>
                    <v-layout row>
                        <v-flex md12>
                            <v-text-field label="Поиск" v-model="searchText"></v-text-field>
                        </v-flex>
                    </v-layout>
                </v-container>
            </v-flex>
            <v-flex v-for="film in searchField" :key="film.id" xs12 sm10 md8 offset-sm1 offset-md2>
                <v-card color="light-blue lighten-3" class="white--text">
                    <v-container>
                        <v-layout row>
                            <v-flex xs3 md2>
                                <v-card-media :src=film.img max-width="100px"></v-card-media>
                            </v-flex>
                            <v-flex xs9 md10>
                                <v-card-title>
                                    <div>
                                        <div class="headline">
                                            {{ film.name }} by {{ film.author }}
                                        </div>
                                        <hr>
                                        <div>
                                            {{ film.description }}
                                        </div>
                                    </div>
                                </v-card-title>
                                <v-card-title>
                                    <v-rating v-model="film.rating"></v-rating>
                                    <span class="ml-2">{{ film.rating }}</span>
                                    <v-spacer></v-spacer>
                                    <v-btn flat nuxt :to="{name: 'info-id', params: { id: film.id }}" dark>info</v-btn>
                                </v-card-title>
                            </v-flex>
                        </v-layout>
                    </v-container>
                </v-card>
            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
export default {
    data(){
        return{
            searchText: null,
            route: '/btn2',
            films:[
                {
                    id: 1,
                    name: 'The Adventures of Tom Sawyer',
                    description: 'Трудно найти того, кто не слышал о захватывающих приключениях Тома Сойера. А читать о них в оригинале еще веселее. Лексика рассказа подойдет даже тем, кто «вчера» начал учить английский. ',
                    author: 'Mark Twain',
                    img: 'tom-sawyer-1.jpeg',
                    rating: 3.5
                },
                {
                    id:2,
                    name: 'Robin Hood',
                    description: 'Нестареющая повесть о храбром лучнике, который борется за справедливость. После прочтения книги можно посмотреть одну из многочисленных экранизаций. ',
                    author: 'Sally M. Stockton',
                    img: 'robin-hood-1.jpg',
                    rating: 5
                },
                {
                    id: 3,
                    name: 'Freckles',
                    description: 'Прекрасный рассказ о девушке-подростке Сьюзи, живущей в тени своей более привлекательной подруги Донны. Сьюзи ненавидит свои веснушки и считает, что они делают ее некрасивой. Узнай, чем закончится история, и изменится ли отношение Сьюзи к самой себе.',
                    author: 'Andrew Mathews',
                    img: 'freckles-1.jpeg',
                    rating: 4
                },
                {
                    id:4,
                    name: 'Ghost of Geenny Castle',
                    description: 'В нашей подборке нашлось место и для истории про призраков. У автора очень яркий стиль повествования, поэтому от рассказа сложно оторваться. Значит, ты запросто осилишь 8 страниц за один подход. ',
                    author: 'John Escott',
                    img: 'ghost-of-geeny-castle-1.jpeg',
                    rating: 4.5
                }
            ]
        }
    },
    computed:{
        searchField(){
            let searchObject = this.films;
            if(this.searchText){
                searchObject = this.films.filter(film => {
                    return film.name.toLowerCase().indexOf(this.searchText.toLowerCase()) >= 0;
                })
            }
            return searchObject;
        }
    }
}
</script>

