<template>
    <div>
      {{clg}}
    </div>
</template>
<script>
export default {
    data() {
        return {
            clg: "Vishwakarma",
        };
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
    }
}
</script>