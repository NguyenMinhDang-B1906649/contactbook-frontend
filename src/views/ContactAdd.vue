<template>
  <div class="page">
    <h4>Thêm Liên hệ</h4>
    <ContactForm isAdd :contact="contact" @add:contact="addContact" />
    <div>{{ message }}</div>
  </div>
</template>
<script>
import ContactForm from "../components/ContactForm.vue";
import ContactService from "../services/contact.service";
export default {
  components: {
    ContactForm,
  },
  data() {
    return {
      contact: {},
      message: "",
    };
  },
  methods: {
    async addContact(data) {
      console.log(data.name);
      try {
        await ContactService.create(data);
        this.message = "Liên hệ được thêm thành công.";
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>
