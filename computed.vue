<template>
    <div>computed:<br><br>

        {{reversemsg}}<br>
        {{reversemsg}}<br>
        {{reversemsg}}<br>
        
        {{now}}<br>
        {{getName}}
        
        <br>
        <label>Find</label>
        <input type="text" v-model="findname"><br>
        <li v-for="names in filterNames" :key="names">
        {{names}}
        </li>
    </div>
</template>
<script>
export default {
    data() {
        return {
            findname:'',
            names:[
                'minaxi',
                'nency',
                'sagar',
                'khushbu',
                'riya',
            ],
            name: "Minaxi Machhi"
            
        };
    },
    computed: {
        reversemsg: function() {
        console.log("computed call");
        return this.name
            .split("")
            .reverse()
            .join("");
        },

        now: function() {
        return Date.now();
        },

        filterNames: function(){
            let filterr = new RegExp(this.findname,'i')
            return this.names.filter(el => el.match(filterr))
        },

        getName: {
            set: function(newValue){
                this.name="minaxi";
            },
            get: function(){
                return this.name
            }
        }
    }
};
</script>
