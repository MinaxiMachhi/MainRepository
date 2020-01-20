<template>
<div id>
  <head>
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css"
    />
  </head>
  <form>
    <h4>REGISTRATION FORM</h4>
    <p class="err-msg" v-if="errors.length">!please fill the details</p>
    
    <div class="form-row">
      <i class="fa fa-user icon"></i>
      <input type="text" v-model.trim="firstname" class="form-input" placeholder="FirstName" />
    </div>
    
    <div class="form-row">
      <i class="fa fa-user icon"></i>
      <input type="text" v-model="lastname" class="form-input" placeholder="LastName" />
    </div>
    
    <div class="form-row">
      <i class="fa fa-envelope icon"></i>
      <input v-model="email" type="email" class="form-input" placeholder="Email" />
    </div>
    
    <div class="form-row">
      <i class="fa fa-number icon"></i>
      <input v-model="phoneno" max="10" type="number" class="form-input" placeholder="Phone No" />
    </div>
    
    <div class="form-row">
      <i class="fa fa-key icon"></i>
      <input v-model="password" type="password" class="form-input" placeholder="Password" />
    </div>
    <div class="form-row">
      <i class="fa fa-key icon"></i>
      <input v-model="password" type="password" class="form-input" placeholder="Confirm Password" />
    </div>

    <div class="radio">
      <label for="gender" class="radio-label">Gender:</label>
      <label class="radio-option">Male</label>
      <input v-model="gender" type="radio" value="Male" class="radio-input" name="gender">
      <label class="radio-option">Female</label>
      <input v-model="gender" type="radio" value="Female" class="radio-input" name="gender">
    </div>
    <div class="checkbox">
      <label for="chkbox" class="chk-label">Technology:</label> 
      <label class="chk-option">Vue</label>
      <input v-model="selected" :options="options"  type="checkbox" value="Vue" class="chk-input" name="Vue">
      <label class="chk-option">React</label>
      <input v-model="selected" type="checkbox" value="React" class="chk-input" name="React">
    </div>

    <label></label>
    <center>
      <button v-on:click.prevent="submitted">Submit</button>
    </center>

    <!-- <p v-for="error in errors" :key="error">{{error}}</p> -->

    <div v-if="issubmitted">
      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
      <p>First Name: {{ data.firstname }}</p>
      <p>Last Name:{{ data.lastname }}</p>
      <p>Email:{{ data.email }}</p>
      <p>Phone No:{{ data.phoneno }}</p>
      <p>Password:{{ data.password }}</p>
      <p>Gender:{{ data.gender }}</p>
        <p>Technology:{{ selected }}</p>
    </div>
  </form>
</div>
</template>
<script>
export default {
  name: "regform",
  data() {
    return {
      errors: [],
      firstname: null,
      lastname: null,
      email: null,
      phoneno: null,
      password: null,
      gender:null,
      issubmitted: false,
      isDisabled: false,
      hasError: true,
      selected:[],
      data: {
        firstname: null,
        lastname: null,
        email: null,
        phoneno: null,
        password: null,
        gender:null,
        selected:null,
      }
    };
  },
  methods: {
    validateForm() {
      this.errors = [];
      if (!this.firstname) {
        this.errors.push("Please Enter FirstName");
      }
      if (!this.lastname) {
        this.errors.push("Please Enter LastName");
      }
      if (!this.phoneno) {
        this.errors.push("Please Enter PhoneNo");
      }
      if (!this.password) {
        this.errors.push("Please Enter Password");
      }

      if (!this.email) {
        this.errors.push("Please Enter Email");
      } else if (!this.validEmail(this.email)) {
        this.errors.push("Valid email required.");
      }

      if (!this.errors.length) {
        return true;
      }
    },
    validEmail: function(email) {
      var re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(email);
    },
    submitted() {
      console.log(this.validateForm());
      if (this.validateForm()) {
        alert("validate");

        this.issubmitted = true;
        /*     console.log(this.firstname)
            console.log(this.lasttname)
            console.log(this.email)
            console.log(this.phoneno)
            console.log(this.password)  */
        this.data = {
          firstname: this.firstname,
          lastname: this.lastname,
          email: this.email,
          phoneno: this.phoneno,
          password: this.password,
          gender: this.gender,
          selected:this.selected,
        };
      } else {
        //
      }
    }
  }
};
</script>

<style>
.form-row {
  display: -ms-flexbox; /* IE10 */
  display: flex;
  width: 100%;
  margin-bottom: 15px;
}
h4 {
  font-size: 2em;
  text-align: center;
  color: rgb(243, 184, 21);
  font-weight: 30;
  text-transform: capitalize;
  letter-spacing: 2px;
  font-family: "Roboto", sans-serif;
}

p {
  font-size: 1em;
  text-align: left;
  color: rgb(18, 98, 202);
  font-weight: 20;
  text-transform: capitalize;
  letter-spacing: 3px;
  font-family: "Roboto", sans-serif;
}
.icon {
  padding: 9px;
  background: dodgerblue;
  color: white;
  min-width: 18px;
  text-align: center;
}
.form-row .form-input {
  width: 100%;
  outline: none;
  border-radius: 0px;
} /*-- main --*/
body {
  font-size: 15px;
  line-height: 1.8;
  color: #222;
  font-weight: 600;
  font-family: "Montserrat";
  background: #c5e9ff;
  padding: 115px 0;
}
button {
  text-transform: uppercase;
  font-size: 0.9em;
  color: #fff;
  background: #76b852;
  outline: none;
  border: 1px solid #76b852;
  cursor: pointer;
  padding: 0.9em;
  width: 100%;
  margin: 2em 0;
  letter-spacing: 4px;
}

button:hover {
  background: #8dc26f;
}
.radio{
  display: -ms-flexbox; /* IE10 */
  display: flex;
  width: 100%;
  background-color: rgb(230, 232, 240);
}
.radio .radio-label{
  float: left;
  width: 10%;
  color:slategray;
}
.radio-option{
  float: left;
  margin-left:100px;
  color:dimgray;
}
.checkbox{
  display: -ms-flexbox; /* IE10 */
  display: flex;
  width: 100%;
  background-color: rgb(230, 232, 240);
}
.checkbox .chk-label{
  float: left;
  width: 10%;
  color:slategray;
}
.chk-option{
  float: left;
  margin-left:100px;
  color:dimgray;
}
.err-msg {
  color: red;
}
</style>