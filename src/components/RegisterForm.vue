<template>
  <div class="form-style-10">
    <h1>
      Sign Up Now!<span>Sign up and tell us what you think of the site!</span>
    </h1>
    <form>
      <div class="section"><span>1</span>First Name & lastName</div>
      <div class="inner-wrap">
        <label
          >First name
          <input type="text" name="field1" v-model="firstName" required
        /></label>
        <div class="error-text-container">
          <span class="error-text" v-if="!validateFirstName"
            >First name is required</span
          >
        </div>

        <label
          >Last name
          <input name="field2" type="text" v-model="lastName" required
        /></label>
        <div class="error-text-container">
          <span class="error-text" v-if="!validateLastName"
            >Last name is required</span
          >
        </div>
      </div>

      <div class="section"><span>2</span>Email & Phone</div>
      <div class="inner-wrap">
        <label
          >Email Address
          <input
            type="email"
            name="field3"
            v-model="email"
            required
            :pattern="emailRegex"
        /></label>
        <div class="error-text-container">
          <span class="error-text" v-if="!validateEmail"
            >Invalid email format</span
          >
        </div>
        <div class="phone">
          <div class="phone-input-container">
            <label
              >3 dig
              <input
                class="dig3"
                type="text"
                name="field4"
                placeholder="05X"
                v-model="phone3"
                required
                :pattern="phone3Regex"
            /></label>
            <div class="error-text-container">
              <span class="error-text" v-if="!validatePhone3"
                >Invalid phone format</span
              >
            </div>
          </div>
          <div class="phone-input-container">
            <label
              >Phone Number (7 dig)
              <input
                class="dig7"
                type="text"
                name="field4"
                v-model="phone7"
                required
                :pattern="phone7Regex"
            /></label>
            <div class="error-text-container">
              <span class="error-text" v-if="!validatePhone7"
                >Invalid phone format</span
              >
            </div>
          </div>
        </div>
      </div>

      <div class="section"><span>3</span>Password</div>
      <div class="inner-wrap">
        <label
          >Password
          <input
            type="password"
            name="field5"
            v-model="password"
            required
            :pattern="passwordRegex"
        /></label>
        <div class="error-text-container">
          <span class="error-text" v-if="!validatePassword"
            >Invalid password format</span
          >
        </div>
      </div>
      <div class="button-section">
        <button
          class="submit-button"
          :disabled="!validateForm()"
          @click.prevent="submitForm"
        >
          submit
        </button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      firstName: "",
      lastName: "",
      email: "",
      phone3: "",
      phone7: "",
      password: "",
      emailRegex: /^[^\s@]+@[^\s@]+\.[^\s@]+$/,
      phone3Regex: /^05\d{1,2}$/,
      phone7Regex: /^\d{7}$/,
      passwordRegex: /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d).{8,}$/,
    };
  },
  computed: {
    validateFirstName() {
      return !!this.firstName;
    },
    validateLastName() {
      return !!this.lastName;
    },
    validateEmail() {
      return this.email.match(this.emailRegex);
    },
    validatePhone3() {
      return this.phone3.match(this.phone3Regex);
    },
    validatePhone7() {
      return this.phone7.match(this.phone7Regex);
    },
    validatePassword() {
      return this.password.match(this.passwordRegex);
    },
  },
  methods: {
    submitForm() {
      if (this.validateForm()) {
        const formData = {
          firstName: this.firstName,
          lastName: this.lastName,
          email: this.email,
          phone3: this.phone3,
          phone7: this.phone7,
          password: this.password,
        };
        console.log("Form is valid, form:", formData);
      } else {
        console.log("Form is not valid");
      }
    },
    validateForm() {
      return (
        this.validateFirstName &&
        this.validateLastName &&
        this.validateEmail &&
        this.validatePhone3 &&
        this.validatePhone7 &&
        this.validatePassword
      );
    },
  },
  //   setup() {
  //     const formData = reactive({
  //       firstName: "",
  //       lastName: "",
  //       email: "",
  //       phone3: "",
  //       phone7: "",
  //       password: "",
  //     });
  //     const rules = {
  //       firstName: { required },
  //       lastName: { required },
  //       email: { required },
  //       phone3: { required },
  //       phone7: { required },
  //       password: { required },
  //     };

  //     const v$ = useVuelidate(rules, formData);
  //     const submitForm = async () => {
  //       const result = await v$.value.$validate();
  //       if (result) {
  //         alert(`horayyyyyyy `);
  //       } else {
  //         alert("form is not valid");
  //       }
  //     };

  //     return { formData, submitForm };
  //   },
};
</script>

<style>
.form-style-10 {
  width: 450px;
  padding: 30px;
  margin: 40px auto;
  background: #fff;
  border-radius: 10px;
  -webkit-border-radius: 10px;
  -moz-border-radius: 10px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.13);
  -moz-box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.13);
  -webkit-box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.13);
}
.form-style-10 .inner-wrap {
  padding: 30px;
  background: #f8f8f8;
  border-radius: 6px;
  margin-bottom: 15px;
}
.form-style-10 h1 {
  background: #2a88ad;
  padding: 20px 30px 15px 30px;
  margin: -30px -30px 30px -30px;
  border-radius: 10px 10px 0 0;
  -webkit-border-radius: 10px 10px 0 0;
  -moz-border-radius: 10px 10px 0 0;
  color: #fff;
  text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.12);
  font: normal 30px "Bitter", serif;
  -moz-box-shadow: inset 0px 2px 2px 0px rgba(255, 255, 255, 0.17);
  -webkit-box-shadow: inset 0px 2px 2px 0px rgba(255, 255, 255, 0.17);
  box-shadow: inset 0px 2px 2px 0px rgba(255, 255, 255, 0.17);
  border: 1px solid #257c9e;
}
.form-style-10 h1 > span {
  display: block;
  margin-top: 2px;
  font: 13px Arial, Helvetica, sans-serif;
}
.form-style-10 label {
  display: block;
  font: 13px Arial, Helvetica, sans-serif;
  color: #888;
  margin-bottom: 7px;
}
.form-style-10 input[type="text"],
.form-style-10 input[type="date"],
.form-style-10 input[type="datetime"],
.form-style-10 input[type="email"],
.form-style-10 input[type="number"],
.form-style-10 input[type="search"],
.form-style-10 input[type="time"],
.form-style-10 input[type="url"],
.form-style-10 input[type="password"],
.form-style-10 textarea,
.form-style-10 select {
  display: block;
  box-sizing: border-box;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  width: 100%;
  padding: 8px;
  border-radius: 6px;
  -webkit-border-radius: 6px;
  -moz-border-radius: 6px;
  border: 2px solid #fff;
  box-shadow: inset 0px 1px 1px rgba(0, 0, 0, 0.33);
  -moz-box-shadow: inset 0px 1px 1px rgba(0, 0, 0, 0.33);
  -webkit-box-shadow: inset 0px 1px 1px rgba(0, 0, 0, 0.33);
}

.form-style-10 .section {
  font: normal 20px "Bitter", serif;
  color: #2a88ad;
  margin-bottom: 5px;
}
.form-style-10 .section span {
  background: #2a88ad;
  padding: 5px 10px 5px 10px;
  position: absolute;
  border-radius: 50%;
  -webkit-border-radius: 50%;
  -moz-border-radius: 50%;
  border: 4px solid #fff;
  font-size: 14px;
  margin-left: -45px;
  color: #fff;
  margin-top: -3px;
}
.form-style-10 input[type="button"],
.form-style-10 input[type="submit"] {
  background: #2a88ad;
  padding: 8px 20px 8px 20px;
  border-radius: 5px;
  -webkit-border-radius: 5px;
  -moz-border-radius: 5px;
  color: #fff;
  text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.12);
  font: normal 30px "Bitter", serif;
  -moz-box-shadow: inset 0px 2px 2px 0px rgba(255, 255, 255, 0.17);
  -webkit-box-shadow: inset 0px 2px 2px 0px rgba(255, 255, 255, 0.17);
  box-shadow: inset 0px 2px 2px 0px rgba(255, 255, 255, 0.17);
  border: 1px solid #257c9e;
  font-size: 15px;
}
.form-style-10 input[type="button"]:hover,
.form-style-10 input[type="submit"]:hover {
  background: #2a6881;
  -moz-box-shadow: inset 0px 2px 2px 0px rgba(255, 255, 255, 0.28);
  -webkit-box-shadow: inset 0px 2px 2px 0px rgba(255, 255, 255, 0.28);
  box-shadow: inset 0px 2px 2px 0px rgba(255, 255, 255, 0.28);
}
.form-style-10 .privacy-policy {
  float: right;
  width: 250px;
  font: 12px Arial, Helvetica, sans-serif;
  color: #4d4d4d;
  margin-top: 10px;
  text-align: right;
}

.phone {
  display: flex;
}
.dig3 {
  width: 50px !important;
}
.dig7 {
  width: 100%;
}
.submit-button {
  background: #2a88ad;
  padding: 8px 20px 8px 20px;
  border-radius: 5px;
  -webkit-border-radius: 5px;
  -moz-border-radius: 5px;
  color: #fff;
  text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.12);
  font: normal 30px "Bitter", serif;
  -moz-box-shadow: inset 0px 2px 2px 0px rgba(255, 255, 255, 0.17);
  -webkit-box-shadow: inset 0px 2px 2px 0px rgba(255, 255, 255, 0.17);
  box-shadow: inset 0px 2px 2px 0px rgba(255, 255, 255, 0.17);
  border: 1px solid #257c9e;
  font-size: 15px;
  cursor: pointer;
}
.submit-button:hover {
  background-color: #1b5a74;
  transition: background-color 0.3s ease;
}
.submit-button:disabled {
  background-color: #a2ccdf;
  cursor: default;
}
.error-text-container {
  margin-bottom: 15px;
}
.error-text {
  color: red;
  font-size: 12px;
}
.phone-input-container {
  display: flex;
  flex-direction: column;
}
</style>
