<template>
    <div>
      {{clg}}
      <p>{{name}}</p>
      <button @click="changeName()">Change Name</button>
    </div>
</template>
<script>
export default {
    data() {
        return {
            clg: "Vishwakarma",
            name:'Minakshi'
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
        name: function(){
            console.log("your name change");
        }
    }
}
</script>