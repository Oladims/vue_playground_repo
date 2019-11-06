<template>
  <div class="template">
    <form action>
      <div class="form-group">
        <label for>Email</label>
        <input
          type="email"
          v-model="userData.email"
          class="form-control"
          name
          id
          aria-describedby="emailHelpId"
          placeholder
        />
        <!-- <small id="emailHelpId" class="form-text text-muted">Help text</small> -->
      </div>
      <div class="form-group">
        <label for>Password</label>
        <input type="password" v-model.lazy="userData.password" class="form-control" name id placeholder />
      </div>
      <div class="form-group">
        <label for>Country</label>
        <select class="form-control" v-model="userData.selectedCountry" :selected="selectedCountry" name id>
          <option
            v-for="(country, index) in userData.countries"
            :selected="country == 'Kenya'"
            :key="index"
          >{{country}}</option>
        </select>
      </div>
      <div class="form-group">
        <h5>Interests</h5>
        <div class="form-check">
          <label class="form-check-label">
            <input
              type="checkbox"
              v-model="userData.interests"
              class="form-check-input"
              name="interests"
              id
              value="Sports"
              checked
            />
            Sports
          </label>
        </div>
        <div class="form-check">
          <label class="form-check-label">
            <input
              type="checkbox"
              v-model="userData.interests"
              class="form-check-input"
              name="interests"
              id
              value="Travel"
              checked
            />
            Travel
          </label>
        </div>
      </div>
      <div class="form-group">
        <h5>Gender</h5>
        <div class="form-check">
          <label class="form-check-label">
            <input
              type="radio"
              class="form-check-input"
              name="gender"
              v-model="userData.gender"
              id
              value="Male"
              checked
            />
            Male
          </label>
        </div>
        <div class="form-check">
          <label class="form-check-label">
            <input
              type="radio"
              class="form-check-input"
              name="gender"
              v-model="userData.gender"
              id
              value="Female"
              checked
            />
            Female
          </label>
        </div>
      </div>
      <div class="form-group">
        <label for>Description</label>
        <textarea class="form-control" name="description" v-model="userData.description" id rows="3"></textarea>
      </div>
      <button @click.prevent="submitForm" type="submit">Submit</button>
    </form>

    <div class="result" v-if="isSubmitted">
      <p>Email: {{userData.email}}</p>
      <p>Password: {{userData.password}}</p>
      <p>Country: {{userData.selectedCountry}}</p>
      <p>Interests: {{userData.interests}}</p>
      <p>Gender: {{userData.gender}}</p>
      <p style="white-space: pre">Description: {{userData.description}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Form",
  data() {
    return {
      userData: {
        email: "olufoworaibrahim@gmail.com",
        password: "",
        countries: ["Nigeria", "Ghana", "Kenya"],
        selectedCountry: "Ghana",
        interests: [],
        gender: "",
        description: "",
      },
        isSubmitted: false,
    };
  },
  methods: {
    submitForm(){
      this.isSubmitted = true;
    },
  },
};
</script>

<style scoped>
.template {
  width: 500px;
  margin: 50px auto;
}
</style>
