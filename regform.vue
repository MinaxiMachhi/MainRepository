<template>
    <div id="app"><h3>REGISTRATION FORM</h3>
	    <div class="main">
            <div class="input">
                <form>
                    <input v-model="firstname" class="text" type="text" placeholder="FirstName"><br>
                    <input v-model="lastname" class="text" type="text" placeholder="LastName"><br>
                    <input v-model="email" vclass="text email" type="text"  placeholder="Email"><br>
                    <input v-model="phoneno" class="text" type="tel" placeholder="Phone No"><br>
                    <input v-model="password" class="text" type="password" placeholder="Password"><br>
                    <center><button v-on:click.prevent="submitted" >Submit</button></center>
                    <div v-if="issubmitted"> 
                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
                        <p>First Name: {{ data.firstname }}</p>
                        <p>Last Name:{{ data.lastname }}</p>
                        <p>Email:{{ data.email }}</p>
                        <p>Phone No:{{ data.phoneno }}</p>
                        <p>Password:{{ data.password }}</p>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'regform',
    data() {
        return {
          firstname: null,
          lastname: null,
          email: null,
          phoneno: null,
          password: null,
          issubmitted: false,
          data: {
            'firstname': null,
            'lastname': null,
            'email': null,
            'phoneno': null,
            'password': null,
        },
      }
    },
  methods: {
      submitted (){
          this.issubmitted = true
    /*     console.log(this.firstname)
        console.log(this.lasttname)
        console.log(this.email)
        console.log(this.phoneno)
        console.log(this.password)  */
        this.data = {
          'firstname': this.firstname,
          'lastname': this.lastname,
          'email': this.email,
          'phoneno': this.phoneno,
         'password': this.password
        }
      }
   }  
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body {
  /* fallback for old browsers */
  background: linear-gradient(to top, #ffffff, #8DC26F);
  background-size: cover;
  background-attachment: fixed;
  font-family: 'Roboto', sans-serif;
}

h3 {
  font-size: 2em;
  text-align: center;
  color: #fff;
  font-weight: 50;
  text-transform: capitalize;
  letter-spacing: 4px;
  font-family: 'Roboto', sans-serif;
}

p{
  font-size: 1em;
  text-align: left;
  color: rgb(18, 98, 202);
  font-weight: 20;
  text-transform: capitalize;
  letter-spacing: 3px;
  font-family: 'Roboto', sans-serif;
}
/*-- main --*/
.main{
  width: 35%;
  margin: 3em auto;
  background: rgba(0, 0, 0, 0.18);
  background-size: cover;
}
.input {
  padding: 3em;
}
input{
  font-size: 0.9em;
  color: #fff;
  width: 94.5%;
  display: block;
  border: none;
  padding: 0.8em;
  border: solid 1px rgba(255, 255, 255, 0.37);
  background: linear-gradient(to bottom, rgba(255, 255, 255, 0) 96%, #fff 4%);
  color: #fff;
  font-family: 'Roboto', sans-serif;
}

button{
  font-size: .9em;
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

input[type="submit"]:hover {
  background: #8DC26F;
}
</style>
