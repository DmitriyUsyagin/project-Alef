<template>
    <div class="person_date">
        <p class="person_date__title">Персональные данные</p>
        <div class="person_date__name">
            <div class="name_in_input">Имя</div>
            <input
                v-model="inputName"
                class="text_in_input"
                type="text"
            />
        </div>
        <div class="person_date__age">
            <div class="name_in_input">Возраст</div>
            <input
                v-model.number="inputAge"
                class="text_in_input"
            />
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            inputName: "",
            inputAge: "",
        };
    },
    emits: ["updatePersonData"],

    watch: {
        inputName(newName) {
            this.$emit("updatePersonData", {
                name: newName,
                age: this.inputAge,
            });
        },
        inputAge(newAge) {
            this.$emit("updatePersonData", {
                name: this.inputName,
                age: newAge,
            });
        },
    },

    computed: {},

    methods: {},

    mounted() {},

    components: {},
};
</script>

<style scoped></style>
