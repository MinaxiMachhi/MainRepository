<template>
    <div>
        {{reversemsg}}<br>
        {{reversemsg}}<br>
        {{reversemsg}}<br>

        {{now}}
    </div>
</template>
<script>
export default {
    data() {
        return {
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
        }
    }
};
</script>
