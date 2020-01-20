<template>
    <div>
        <br>watcher
        <br>
      {{clg}}
      <p>{{name}}</p>

        <input v-model="tech"> 
        {{techname}}<br><br>

      <button @click="changeName()">Change Name</button><br><br>
    </div>
</template>
<script>
export default {
    data() {
        return {
            clg: "Vishwakarma",
            name:'Minakshi',
            tech:'',
            techname:''
        };
    },
    methods:{
        changeName(){
            this.name='Minaxi';
        }
    },
    mounted() {
        setTimeout(() => {
            console.log("============clg channge");
            this.clg = "VGEC";
        }, 5000);
    },
    watch: {
        clg: function(val) {
            console.log("watch call", val);
        },
        name: function(newValue,oldValue){
            //console.log(this.name.split('').reverse().join(''));
            console.log(newValue,oldValue);
            console.log('==========your name change======');
        },
        tech: function(){
            this.techname=this.tech.toUpperCase();
            console.log("watch");
        }
    }
}
</script>