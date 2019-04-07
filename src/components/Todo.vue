<template>
    <v-container v-if="!todo.deleted">
        <v-layout >
            <v-card :color="isCompleted()">
                <v-card-title>
                    TODO!
                </v-card-title>
                <v-card-text>
                    <v-text-field :disabled="!isEditClick" v-model="todo.todo">
                    </v-text-field>
                </v-card-text>
                <v-card-actions>
                    <v-btn round @click="completed()" color="green">Completed</v-btn>
                    <v-btn round @click="change()" color="blue">Edit</v-btn>
                    <v-btn round @click="deleted()" color="red">Delete</v-btn>
                </v-card-actions>
            </v-card>
        </v-layout>
    </v-container>
        
</template>

<script>
export default {
    name: 'Todo',
    props:{
        todo:Object
    },
    data() {
        return {
            isEditClick:false,
        }
    },
    methods: {
        completed(){
            this.todo.completed=!this.todo.completed;
        },
        change(){
            this.isEditClick =!this.isEditClick; 
        },
        deleted(){
            this.todo.deleted=true;
        },
        isCompleted(){
            if(this.todo.completed){
                return 'green'
            }else{
                return 'red'
            }
        }
    },
}
</script>

<style scoped>

</style>

