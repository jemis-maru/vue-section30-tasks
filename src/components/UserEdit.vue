<template>
    <div class="component">
        <h3>You may edit the User here</h3>
        <p>Edit me!</p>
        <p>User Age: {{ age }}</p>
        <button @click="editAge">Edit Age</button>
    </div>
</template>

<script>
    import {eventBus} from '../main';

    export default {
        props: ['userAge'],
        data: function(){
            return{
                age: null,
            };
        },
        methods: {
            editAge() {
                // const userAge = 30;
                this.age = 30;
                // this.$emit('ageWasEdited', userAge);
                // eventBus.$emit('ageWasEdited', this.userAge);
                eventBus.changeAge(this.age);
            }
        },
        computed: {
            myAge(){
                this.age = this.userAge;
                return this.age;
            },
        },
        created() {
            this.myAge;
        }
    }
</script>

<style scoped>
    div {
        background-color: lightgreen;
    }
</style>
