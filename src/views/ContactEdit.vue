<template>
    <div v-if="contact" class="page">
    <h4>Hiệu chỉnh liên hệ</h4>
    <ContactForm
        :contact="contact"
        @submit:contact="updateContact"
        @delete:contact="deleteContact"
    />
    <p>{{ message }}</p>
    </div>
</template>

<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.services";

export default{
    components:{
        ContactForm,
    },
    props: {
        id: {type: String, required: true},
    },
    data(){
        return {
            contact: null,
            message: "",
        };
    },
    methods: {
        async getContact(id){
            try{
                this.contact = await ContactService.get(id);
            } catch (error){
                console.log(error);
                //Chuyen sang trang notfound dong thoi giu cho URl khong doi
                this.$router.push({
                    name: "notfound",
                    params: {
                        pathwatch: this.$route.path.split("/").slice(i)
                    },
                    query: this.$route.query,
                    hash: this.$route.hash,
                });
            }
        },
        async updateContact(data){
            try {
                await ContactService.update(this.contact._id, data);
                this.message = "Liên hệ được cập nhật thành công.";
            } catch(error){
                console.log(error);
            }
        },
        async deleteContact(){
            if (confirm("Bạn muốn xóa liên hệ này?")){
                try{
                    await ContactService.delete(this.contact._id);
                    this.$router.push({name: contactbook});
                }catch (error){
                    console.log(error);
                }
            }
        },
    },
    created(){
        this.getContact(this.id);
        this.message = "";
    },
};
</script>