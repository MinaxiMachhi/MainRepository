<template>
  <div>
    Name:
    <input type="text" ref="name" v-model="name" />
    <br />
    <br />address:
    <input type="text" ref="address" v-model="address" />
    <br />
    <br />
    <input type="button" @click.prevent="checkName()" value="submit" />
    <br />
    <br />Email:
    <input type="email" ref="email" v-model="email" />
    <input type="button" @click.prevent="checkEmail()" value="submit" />
    <br />

    <div v-if="isSubmitted">{{email}}</div>
    <br />

    <select ref="select" @click="getValue">
      <option value="BMW">BMW</option>
      <option value="Mercedes">Mercedes</option>
      <option value="Audi">Audi</option>
      <option value="Hyundai">Hyundai</option>
    </select>
    <br />
    You select {{value}} :)
    <br><br>
    
    <p v-for='no in 10' :key="no" ref='no'>This is no {{no}} *2= {{no*2}}</p>
    <input type="button" value="submit" @click="mul()">
    
  </div>
</template>
<script>
export default {
  data() {
    return {
      name: "",
      address: "",
      email: "",
      isSubmitted: false,
      value: null,
    };
  },
  methods: {
    checkName() {
      if (this.name == "bacancy" && this.address == "bacancy") {
        this.$refs.name.className = "green"; //using classname
        this.$refs.address.className = "green";
      } else {
        this.$refs.name.className = "red";
        this.$refs.address.className = "red";
      }

      // console.log(this.$refs);
      console.log(this.$refs.name.baseURI); //baseURI
    },
    checkEmail() {
      if (
        !this.email.match(
          /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,24}))$/
        )
      ) {
        this.$refs.email.style = "border-color:red"; //using style
      } else {
        this.$refs.email.style = "border-color:green";
        this.issubmitted = true;
      }
    },

    getValue() {
      this.value = this.$refs.select.value;
    },
    mul(){
      console.log(this.$refs);
    }
  }
};
</script>

<style scoped>
.red {
  border-color: red;
}
.green {
  border-color: green;
}
</style>