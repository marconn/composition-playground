<template>
    <section class="container">
        <user-data
            class="test"
            :first-name="firstName"
            :last-name="lastName"
            :age="age"
        ></user-data>
        <button @click="setAge">Change Age</button>
        <div>
            <input type="text" placeholder="First Name" v-model="firstName" />
            <input type="text" placeholder="Last Name" ref="lastNameInput" />
            <button @click="setLastName">Set Last Name</button>
        </div>
    </section>
</template>

<script>
// import { ref, computed, watch, provide } from 'vue';
import UserData from './components/UserData.vue';

export default {
    components: {
        UserData,
    },
    data() {
        return {
            firstName: 'Roland',
            lastName: 'Cambridge',
            age: 31,
        };
    },
    methods: {
        setNewAge() {
            this.age = 32;
        },
        setLastName() {
          this.lastName = this.$refs['lastNameInput']
          this.$set(this.adress, 'Llano los Angeles');
        }
    },
    watch: {
        age(val) {
            console.log(val);
        },
    },
    provide() {
        return { userAge: this.age };
    },
};
</script>

<style>
* {
    box-sizing: border-box;
}

html {
    font-family: sans-serif;
}

body {
    margin: 0;
}

.container {
    margin: 3rem auto;
    max-width: 30rem;
    border-radius: 12px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    padding: 1rem;
    text-align: center;
}
</style>
