<template>
  <div class="container">
    <div class="row justify-content-center">
      <div class="col-12 col-md-6">
        <div class="card">
          <div class="card-body text-left">
            <div class="row">
              <div class="col">
                <div class="form-group">
                  <label for="username">Username</label>
                  <input
                  @keyup="validateUsername"
                  v-model="username"
                  :class="{ 'is-valid': isValidUsername, 'is-invalid': isInvalidUsername }"
                  id="username" placeholder="username" type="text" class="form-control">
                  <div class="valid-feedback">
                    <span>Looks good!</span>
                  </div>
                  <div class="invalid-feedback">
                    <span>{{ invalidUsernameText }}</span>
                  </div>
                </div>
              </div>
            </div>
            <div class="row">
              <div class="col">
                <div class="form-group">
                  <label for="password">Password</label>
                  <input
                  @keyup="validatePassword"
                  v-model="password"
                  :class="{ 'is-invalid': isInvalidPassword, 'is-valid': isValidPassword }"
                  id="password" placeholder="password" type="password" class="form-control">
                  <div class="invalid-feedback">
                    <span>{{ invalidPasswordText }}</span>
                  </div>
                  <div class="valid-feedback">
                    <span>Looks good!</span>
                  </div>
                </div>
              </div>
            </div>
            <div class="row">
              <div class="col text-right">
                <button
                @click="onSubmit"
                class="btn btn-primary" type="button">Login now!</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      username: null,
      password: null,
      isInvalidPassword: false,
      isValidPassword: false,
      isValidUsername: false,
      isInvalidUsername: false,
      invalidPasswordText: null,
      invalidUsernameText: null,
    }
  },
  methods: {
    onSubmit: function() {
      this.validateUsername()
      this.validatePassword()
    },
    validateUsername: function() {
      if(this.username != null) {
        if(this.username.length > 0) {
          this.isValidUsername = true
          this.isInvalidUsername = false
        }else {
          this.invalidUsernameText = 'username must be > 0 character'
          this.isValidUsername = false
          this.isInvalidUsername = true
        }
      }else {
        this.invalidUsernameText = 'this field is required'
        this.isValidUsername = false
        this.isInvalidUsername = true
      }
    },
    validatePassword: function() {
      if(this.password != null) {
        if(this.password.length < 6 || 
        this.password.length > 12) {
          this.invalidPasswordText = 'password must be 6 - 12 characters'
          this.isInvalidPassword = true
          this.isValidPassword = false
        }else {
          this.isValidPassword = true
          this.isInvalidPassword = false
        }
      }else {
        this.invalidPasswordText = 'this field is required'
        this.isValidPassword = false
        this.isInvalidPassword = true
      }
    }
  }
}
</script>
