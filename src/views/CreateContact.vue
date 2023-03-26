<template>
    <div class="page">
        <h4>Tạo Liên Hệ Mới</h4>
        <CreateContact @submit:contact="createContact" />
        {{ message }}
    </div>
</template>
<script>
import CreateContact from "@/components/CreateContact.vue";
import ContactService from "@/services/contact.service";
export default {
    components: {
        CreateContact,
    },

    data() {
        return {
            message: "",
        };
    },
    methods: {
        async createContact(data) {
            try {
                await ContactService.create(data);
                this.message = "Liên hệ được tạo thành công.";
            } catch (error) {
                console.log(error);
            }
        },
    },
    created() {
        this.message = "";
    },
};
</script>
