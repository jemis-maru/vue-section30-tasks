<template>
    <div class="component">
        <h3>You may view the User Details here</h3>
        <p>Many Details</p>
        <p>User Name: {{ switchName() }}</p>
        <p>User Age: {{ age }}</p>
        <button @click="resetName">Reset Name</button>
        <button @click="resetFn()">Reset Name</button>
    </div>
</template>

<script>
    import { eventBus } from '../main';

    export default {
        props: {
            myName: {
                type: String
            },
            resetFn: Function,
            userAge: Number
        },
        data: function(){
            return{
                age: null,
            };
        },
        methods: {
            switchName() {
                return this.myName.split("").reverse().join("");
            },
            resetName() {
                // this.myName = 'Jemis';
                const name = 'Jemis';
                this.$emit('nameWasReset', name);
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
            eventBus.$on('ageWasEdited', (age) => {
                this.age = age;
            });
        }
    }
</script>

<style scoped>
    div {
        background-color: lightcoral;
    }
</style>
