<template>
    <header class="header">
        <div class="header_logo">
            <div class="logo">
                <img
                    class="logo_alef"
                    src="https://midas.alef.im/manual_resources/Logo.png"
                    alt="logo"
                />
            </div>
        </div>
        <nav class="header_right">
            <button
                @click="goToPage('one')"
                class="one_page"
            >
                Форма
            </button>
            <button
                @click="goToPage('two')"
                class="two_page"
            >
                Превью
            </button>
        </nav>
    </header>
</template>

<script>
export default {
    emits: ["change-page"],
    data() {
        return {};
    },

    computed: {},

    methods: {
        goToPage(page) {
            this.$emit("change-page", page);
        },
    },

    mounted() {},

    components: {},
};
</script>

<style scoped></style>
