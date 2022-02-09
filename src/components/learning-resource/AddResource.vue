<template>
    <base-dialog v-if="inputEmpty" @close="closeDialogFun">
        <template #default>
            <p>Input field is required.</p>
        </template>
        <template #actions>
            <base-button @click="closeDialogFun">Close</base-button>
        </template>
    </base-dialog>
    <base-card>
        <form action="" @submit.prevent="submitFormData">
            <div class="form-control">
                <label for="title">Title</label>
                <input id="title" name="title" type="text" ref="titleInput">
            </div>
            <div class="form-control">
                <label for="description">Description</label>
                <textarea name="description" id="description" rows="3" ref="descInput"></textarea>
            </div>
            <div class="form-control">
                <label for="link">Description</label>
                <input name="link" id="link" type="url" ref="urlInput">
            </div>
            <div>
                <base-button type="submit">Add Resource</base-button>
            </div>
        </form>
    </base-card>
</template>

<script>
    export default {
        inject: ['addRes'],
        data(){
            return{
                inputEmpty: false,
            };
        },
        methods:{
            submitFormData(){
                const formTitle = this.$refs.titleInput.value;
                const formDesc = this.$refs.descInput.value;
                const formUrl= this.$refs.urlInput.value;

                if(formTitle.trim() === '' || formDesc.trim() === '' || formUrl.trim() === ''){
                    this.inputEmpty = true;
                    return;
                }

                this.addRes(formTitle, formDesc, formUrl);
            },
            closeDialogFun(){
                this.inputEmpty = false;
            },
        },
    }
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>