<template>
  <div class="col-6 offset-3 ">
        <h4>Thêm  Liên hệ</h4>
        <ContactForm
            :contact="contact"
            @submit:contact="AddContact"
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
      data() {
        return {
            contact: {},
            message: "",
        };
    },
    methods: {
       

    async AddContact(data) {
        try {
            this.contact = await ContactService.create(data);
            this.message = "Liên hệ được thêm thành công.";
        } catch (error) {
            console.log(error);
        }
    },
   
},

};
</script> 
