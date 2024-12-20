<template>
    <div class="children">
        <div class="children_title">
            <p class="children_title__title">Дети ( макс. 5)</p>
            <button
                @click="addChild"
                class="children__button"
                v-if="this.children.length < 5"
            >
                Добавить ребенка
            </button>
        </div>
        <div
            v-for="(child, index) in children"
            :key="index"
            class="row_child"
        >
            <div class="child_name">
                <div class="name_in_input">Имя</div>
                <input
                    class="text_in_input"
                    type="text"
                    v-model="child.name"
                />
            </div>
            <div class="child_age">
                <div class="name_in_input">Возраст</div>
                <input
                    class="text_in_input"
                    type="text"
                    v-model.number="child.age"
                />
            </div>
            <button
                @click="delRowChild(index)"
                class="child_del"
            >
                Удалить
            </button>
        </div>
    </div>
</template>

<script>
import { handleError } from "vue";

export default {
    emits: ["aaaaa"],
    data() {
        return {
            children: [],
        };
    },

    computed: {},

    methods: {
        addChild() {
            const emptyChild = { name: "", age: null };
            if (this.children.length < 5) {
                this.children.push({ emptyChild });
            }
        },
        delRowChild(index) {
            this.children.splice(index, 1);
        },
    },

    emits: ["updateChildrenData"],

    watch: {
        children: {
            handler(newChildren) {
                this.$emit("updateChildrenData", newChildren);
            },
            deep: true,
        },
    },

    mounted() {},

    components: {},
};
</script>

<style scoped></style>
