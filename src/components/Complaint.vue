<template>
  <div class="container">
    <form>
      <div class="row">
        <div
          class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3"
        >
          <h1>File a Complaint</h1>
          <hr />
          <div class="form-group">
            <label for="email">Mail</label>
            <input
              type="text"
              id="email"
              class="form-control"
              v-model.lazy.trim="userData.email"
            />
          </div>
          <div class="form-group">
            <label for="password">Password</label>
            <input
              type="password"
              id="password"
              class="form-control"
              v-model.lazy.trim="userData.password"
            />
          </div>
          <div class="form-group">
            <label for="age">Age</label>
            <input
              type="number"
              id="age"
              class="form-control"
              v-model.lazy.number="userData.age"
            />
          </div>
        </div>
      </div>
      <div class="row">
        <div
          class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group"
        >
          <label for="message">Message</label>
          <br />
          <!-- Interpolation between <textarea>{{ test }}</textarea> doesn't work!-->
          <textarea
            id="message"
            rows="5"
            class="form-control"
            placeholder="Enter your message..."
            v-model.lazy="message"
          ></textarea>
        </div>
      </div>
      <div class="row">
        <div
          class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3"
        >
          <div class="form-group">
            <label for="sendmail">
              <input
                type="checkbox"
                id="sendmail"
                value="SendMail"
                v-model="sendMail"
              />
              Send Mail
            </label>
            <label for="sendInfomail">
              <input
                type="checkbox"
                id="sendInfomail"
                value="SendInfoMail"
                v-model="sendMail"
              />
              Send Infomail
            </label>
          </div>
        </div>
      </div>
      <div class="row">
        <div
          class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group"
        >
          <label for="male">
            <input type="radio" id="male" value="Male" v-model="gender" /> Male
          </label>
          <label for="female">
            <input type="radio" id="female" value="Female" v-model="gender" />
            Female
          </label>
        </div>
      </div>
      <div class="row">
        <div
          class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 from-group"
        >
          <label for="priority">Priority</label>
          <select id="priority" class="form-control" v-model="selectedPriority">
            <option v-for="priority in priorities" :key="priority">
              {{ priority }}
            </option>
          </select>
        </div>
      </div>
      <hr />
      <div class="row">
        <div
          class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3"
        >
          <AppSwitch :isOn="isOn" v-model="isOn" />
        </div>
      </div>
      <div class="row">
        <div
          class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3"
        >
          <button class="btn btn-primary" @click.prevent="handleSubmit">
            Submit!
          </button>
        </div>
      </div>
    </form>
    <hr />
    <div class="row" v-if="isSubmitted">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <div class="panel panel-default">
          <div class="panel-heading">
            <h4>Your Data</h4>
          </div>
          <div class="panel-body">
            <p>Mail: {{ userData.email }}</p>
            <p>Password: {{ userData.password }}</p>
            <p>Age: {{ userData.age }}</p>
            <p>Message: {{ message }}</p>
            <p>
              <strong>Send Mail?</strong>
            </p>
            <ul>
              <li v-for="item in sendMail" :key="item">{{ item }}</li>
            </ul>
            <p>Gender: {{ gender }}</p>
            <p>Priority: {{ selectedPriority }}</p>
            <p>Switched: {{ isOn ? 'On' : 'Off' }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Switch from './Switch';

export default {
  components: {
    AppSwitch: Switch
  },
  data() {
    return {
      userData: {
        email: null,
        password: null,
        age: null
      },
      message: null,
      sendMail: [],
      gender: null,
      selectedPriority: null,
      priorities: ['High', 'Medium', 'Low'],
      isOn: true,
      isSubmitted: false
    };
  },
  methods: {
    handleSubmit() {
      this.isSubmitted = true;
    }
  }
};
</script>

<style></style>
