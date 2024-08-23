<template>
  <base-dialog v-if="invalidInput" title="Invalid Input" @close="confirmError">
    <template #default>
      <p>Unfortunately atleast one input feild is invalid.</p>
      <p>
        Please check all inputs and make sure you entered a few characters into
        each input feild.
      </p>
    </template>
    <template #actions>
      <base-button @click="confirmError"> Okay</base-button>
    </template>
  </base-dialog>
  <base-card>
    <form @submit.prevent="submitData">
      <div class="form-control">
        <label for="title"> Title </label>
        <input id="title" type="text" name="title" ref="titleInput" />
      </div>
      <div class="form-control">
        <label for="description"> Description </label>
        <textarea
          id="description"
          type="text"
          name="description"
          rows="3"
          ref="descInput"
        ></textarea>
      </div>
      <div class="form-control">
        <label for="link"> Link </label>
        <input id="link" type="url" name="link" ref="linkInput" />
      </div>
      <div>
        <base-button type="submit"> Add Resource</base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
import BaseDialog from '../UI/BaseDialog.vue';
export default {
  components: { BaseDialog },
  inject: ['addNewResource'],
  data() {
    return {
      invalidInput: false,
    };
  },
  methods: {
    submitData() {
      let enteredTitle = this.$refs.titleInput.value;
      let enteredDesc = this.$refs.descInput.value;
      let enteredLink = this.$refs.linkInput.value;

      if (
        enteredTitle.trim() === '' ||
        enteredDesc.trim() === '' ||
        enteredLink.trim() === ''
      ) {
        this.invalidInput = true;
        return;
      }

      this.addNewResource(enteredTitle, enteredDesc, enteredLink);
    },
    confirmError() {
      this.invalidInput = false;
    },
  },
};
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

.error-field {
  border: 1px solid red;
}
</style>
