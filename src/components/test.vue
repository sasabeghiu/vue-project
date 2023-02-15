<template>
    <div>
        <h1>{{ student.name }}</h1>
        <h1 v-if="student.age > 18" class="header">you're old enough</h1>
        <h1 v-if="student.age < 18" class="header">you're not old enough</h1>

        <h1 :class="{ 'old': student.age > 18, 'young': student.age < 18 }">some content</h1>
        <input type="text" name="" v-model="student.age">

        <button @click="doSomething()">Click me (or not)</button>
    </div>
</template>

<script>
export default {
    name: "test",
    data() {
        return {
            secretcode: "q1w2e3",
            student: {
                name: "Sashito",
                age: 24
            }
        }
    },
    props: {
        message: String
    },
    methods: {
        doSomething() {
            alert("I hate alerts");
        }
    },
    mounted() {
        this.doSomething();
    }
}
</script>

<style scoped>
.old {
    color: blue
}

.young {
    color: red
}
</style>