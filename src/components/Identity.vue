<template>
  <div>
    <form v-if="!isSuccess">
      <div class="form-group">
        <label for="firstName">First Name *</label>
        <input
          type="text"
          id="firstName"
          class="form-control"
          v-model.lazy.trim="userIdentity.firstName"
        />
      </div>
      <div class="form-group">
        <label for="lastName">Last Name *</label>
        <input
          type="text"
          id="lastName"
          class="form-control"
          v-model.lazy.trim="userIdentity.lastName"
        />
      </div>
      <div class="form-group">
        <label for="male">
          <input type="radio" id="male" value="Male" v-model="gender" /> Male
        </label>
        <label for="female">
          <input type="radio" id="female" value="Female" v-model="gender" />
          Female
        </label>
      </div>
      <div class="alert alert-danger" v-if="!isValid">
        Please enter required fields
        <button type="button" class="close" @click="isValid = true">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <button class="btn btn-primary" @click.prevent="handleFormSubmit">Submit</button>
    </form>
    <div class="alert alert-success" v-if="isSuccess">
      <h4 class="alert-heading">Success!</h4>
      <hr />
      <p>First: {{ userIdentity.firstName }}</p>
      <p>Last: {{ userIdentity.lastName }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      userIdentity: {
        firstName: "",
        lastName: ""
      },
      isValid: true,
      isSuccess: false
    };
  },
  methods: {
    handleFormSubmit() {
      if (
        (!this.userIdentity.firstName && !this.userIdentity.firstName.length) ||
        (!this.userIdentity.lastName && !this.userIdentity.lastName.length)
      ) {
        this.isValid = false;
      } else {
        this.isSuccess = true;
      }
    }
  }
};
</script>

<style>
.alert {
  padding-top: 5px;
  padding-bottom: 5px;
}
</style>
