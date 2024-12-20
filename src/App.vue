<template>
    <div class="container">
        <div class="wrapper">
            <app-header @change-page="changePage"></app-header>
            <div
                class="content"
                v-if="currentPage === 'one'"
            >
                <app-person @update-person-data="updatePersonData"></app-person>
                <app-children
                    @update-children-data="updateChildrenData"
                ></app-children>
                <div class="save">
                    <button
                        @click="saveData"
                        class="content__button"
                    >
                        Сохранить
                    </button>
                </div>
            </div>
            <div v-else-if="currentPage === 'two'">
                <div class="content">
                    <div class="person_date">
                        <p class="person_date__title">Персональные данные</p>
                        <div class="person_date_prewiew">
                            {{ personData.name }}, {{ personData.age }} лет
                        </div>
                        <div class="children_date_prewiew">
                            <p class="children_date__title">Дети</p>
                            <ul
                                class="row_child__name"
                                v-for="(child, index) in childrenData"
                                :key="index"
                            >
                                <li>{{ child.name }}, {{ child.age }} лет</li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
            <app-footer></app-footer>
        </div>
    </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import AppPerson from "./components/AppPerson.vue";
import AppChildren from "./components/AppChildren.vue";
import AppFooter from "./components/AppFooter.vue";

export default {
    data() {
        return {
            currentPage: "one",
            personData: {
                name: "",
                age: "",
            },
            childrenData: [],
        };
    },
    methods: {
        changePage(page) {
            this.currentPage = page;
        },
        updatePersonData(data) {
            this.personData = { ...data };
        },
        updateChildrenData(children) {
            this.childrenData = children;
        },
        saveData() {
            this.currentPage = "two";
        },
    },
    components: { AppHeader, AppPerson, AppChildren, AppFooter },
};
</script>

<style></style>
