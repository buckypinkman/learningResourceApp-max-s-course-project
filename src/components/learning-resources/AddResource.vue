<template>
    <div>
        <modal-dialog v-if="inputIsInvalid" title="Invalid Input!" @close="confirmError">
            <template #default>
                <p>Please fill all input field.</p>
                <p>Enter at least a few characters to each input field.</p>
            </template>
            <template #actions>
                <base-button @click="confirmError">Okay</base-button>
            </template>
        </modal-dialog>
            
        <base-card>
            <form @submit.prevent="submitData">
                <div class="input-group">
                    <label for="title">Title</label>
                    <input type="text" id="title" ref="titleInput" autocomplete="off">
                </div>
                <div class="input-group">
                    <label for="description">Description</label>
                    <textarea id="description" cols="20" rows="4" ref="descInput"></textarea>
                </div>
                <div class="input-group">
                    <label for="link">Link</label>
                    <input type="url" id="link" ref="urlInput">
                </div>
                <base-button type="submit">Add Resource</base-button>
            </form>
        </base-card>
    </div>
    
</template>

<script>
    export default {
        inject: ['addResource'],
        data() {
            return {
                inputIsInvalid: false
            }
        },
        methods: {
            submitData() {
                const title = this.$refs.titleInput.value
                const description = this.$refs.descInput.value
                const link = this.$refs.urlInput.value

                if(title.trim() == '' || description.trim() == '' || link.trim() == '') {
                    this.inputIsInvalid = true
                    return;
                }
                this.addResource(title,description,link)
            },
            confirmError() {
                this.inputIsInvalid = false
            }
        }

    }
</script>

<style scoped>
    label {
        font-weight: 500;
        display: block;
        margin-bottom: 0.5rem;
    }
    input,
    textarea {
        display: block;
        width: 100%;
        font: inherit;
        padding: 0.5rem;
        border: 1px solid #ccc;
        border-radius: 3px;
        transition: .15s;
    }
    input:focus,
    textarea:focus {
        outline: none;
        border-color: #3a0061;
        background-color: #f7ebff;
    }
    .input-group {
        margin-bottom: 1rem;
    }
    
</style>