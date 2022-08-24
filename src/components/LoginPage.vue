<template>
  <div class="bg">
    <div class="card-bg">
      <div class="card">
        <div class="card-items"><h1>Join the community</h1></div>

        <div class="card-items">
          <p>
            Take your art to the next level. Get it seen by millions of people.
          </p>
        </div>
        <div class="card-items">
          <button><p>Join with Facebook</p></button>
        </div>
        <span class="card-items">Or</span>
        <form>
          <div class="form-container card-items">
            <div class="form-items">
              <div class="name-container">
                <input
                  class="pad"
                  type="text"
                  placeholder="First name"
                  name=""
                  id="name"
                  v-model.trim="$v.firstname.$model"
                  :class="{
                    'is-invalid': $v - firstname.$error,
                    'is-valid': !$v.firstname.$invalid,
                  }"
                />

                <input
                  type="text"
                  placeholder="Surname"
                  name=""
                  id="surname"
                  v-model.trim="$v.lastname.$model"
                  :class="{
                    'is-invalid': $v - lastname.$error,
                    'is-valid': !$v.lastname.$invalid,
                  }"
                />
                <div class="invalid-feedback">
                  <span v-if="!$v.firstname.required">Enter your name *</span>
                  <span v-if="!$v.firstname.minLength"
                    >Your name must be longer than
                    {{ $v.firstname.$params.minLength.min }}
                  </span>
                  <span v-if="!$v.firstname.maxLength">
                    Your name must be less than
                    {{ $v.firstname.$params.maxLength.max }}
                  </span>
                </div>
                <div class="invalid-feedback">
                  <span v-if="!$v.lastname.required">Enter your surname *</span>
                  <span v-if="!$v.lastname.minLength"
                    >Your surname must be longer than
                    {{ $v.lastname.$params.minLength.min }}</span
                  >
                  <span v-if="!$v.lastname.maxLength"
                    >Your surname must be less than
                    {{ $v.lastname.$params.maxLength.max }}
                  </span>
                </div>
              </div>
            </div>
            <div class="form-items">
              <input
                placeholder="Email"
                type="email"
                v-model.trim="$v.email.$model"
                :class="{
                  'is-invalid': $v.email.$error,
                  'is-valid': !$v.email.$invalid,
                }"
              />
              <div class="invalid-feedback">
                <span v-if="!$v.email.required">Enter your Email*</span>
                <span v-if="!$v.email.email">Email must be valid</span>
              </div>
            </div>
            <div class="form-items">
              <input
                type="password"
                placeholder="Password"
                name=""
                id=""
                v-model.trim="$v.password.$model"
                :class="{
                  'is-invalid': $v - password.$error,
                  'is-valid': !$v.password.$invalid,
                }"
              />
              <div class="invalid-feedback">
                <span v-if="!$v.password.required">Enter your password *</span>
                <span v-if="!$v.password.minLength"
                  >Your password must be longer than
                  {{ $v.password.$params.minLength.min }}
                </span>
              </div>
            </div>
          </div>
          <button type="submit"><p>Create New Account</p></button>
        </form>
        <span class="card-items"
          >By joining, you agree to our Terms of Service and Privacy
          Policy</span
        >
      </div>
    </div>
  </div>
</template>

<script>
import {
  required,
  minLength,
  maxLength,
  email,
  numeric,
} from "vuelidate/lib/validators";
export default {
  name: "FormValidation",
  data() {
    return {
      firstname: "",
      lastname: "",
      email: "",
      password: "",
    };
  },
  validations: {
    firstname: {
      required,
      minLength: minLength(3),
      maxLength: maxLength(10),
      numeric,
    },
    lastname: {
      required,
      minLength: minLength(3),
      maxLength: maxLength(10),
    },
    email: {
      required,
      email,
    },
    password: {
      required,
      minLength: minLength(6),
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.bg {
  width: 100%;
  height: 100%;
  background-color: #f4f9ff;
  display: flex;
  justify-content: center;
  padding: 50px;
  .card-bg {
    width: 33%;
    height: 100%;
    background: #e8f1fd;
    border-radius: 30px;
    padding: 30px;
    .card {
      width: 100%;
      height: 100%;
      border-radius: 20px;
      background-color: #ffff;
      box-shadow: 0px 22px 35px rgba(5, 27, 105, 0.12);
      padding: 40px 70px;
      text-align: center;
      span {
        display: block;
        opacity: 0.5;
      }
      .card-items {
        margin-top: 10px;
        button {
          width: 100%;
          padding: 10px;
          border: none;
          border-radius: 5px;
          background-color: #4968ad;
          &:hover {
            cursor: pointer;
          }
          p {
            color: #ffff;
            font-size: 13px;
          }
        }
      }
      h1 {
        font-family: sans-serif;
        font-size: 29px;
        line-height: 30px;
      }
      form {
        input {
          padding: 8px 18px;
        }
        button {
          width: 100%;
          padding: 10px;
          border: none;
          border-radius: 5px;
          background-color: #1e2c4b;
          &:hover {
            cursor: pointer;
          }
          p {
            color: #ffff;
            font-size: 12px;
          }
        }
      }
      .form-container {
        .form-items {
          margin-bottom: 10px;
          input {
            width: 100%;
            outline: none;
            padding: 13px;
            border: 1px solid #e8f1fd;
          }
          span {
            color: rgb(195, 6, 6);
          }
        }
      }
      .name-container {
        #name,
        #surname {
          width: 48%;
        }
        #name {
          margin-right: 9px;
        }
      }
    }
  }
}
</style>
