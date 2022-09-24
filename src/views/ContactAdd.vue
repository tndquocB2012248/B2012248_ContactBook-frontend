<template>
    <div v-if="contact" class="page">
        <h4 class="addText">Thêm Liên Hệ</h4>
            <ContactForm
            :contact="contact"
            @submit:contact="addContact"
        />
        <p>{{ message }}</p>
    </div>
</template>

<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";

export default {
    components: {
        ContactForm,
    },
    props: {
        id: { type: String, required: true },
    },
    data() {
        return {
            contact: {
                name: '',
            },
            message: "",
        };
    },
    methods: {
        async addContact(data) {
            try {
                this.contact = await ContactService.create(data);
                this.message = "Liên hệ được thêm thành công.";
            } catch (error) {
                console.log(error);
            }
        },
    },
    created() {
        this.addContact(this.data);
        this.message = "";
    },
};
</script>

<style scoped>
    .addText {
        margin-top: 1rem;
        margin-bottom: 1rem;
    }
</style>