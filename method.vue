<template>
    <div>
        methods:<br>
        {{reversemsg()}}<br>
        {{reversemsg()}}<br>
        {{reversemsg()}}
    </div>
</template>
<script>
export default {
    data() {
        return {
        name: "Minaxi Machhi"
        };
    },
    methods: {
        reversemsg: function() {
        console.log("method call");
        return this.name
            .split("")
            .reverse()
            .join("");
        },
    }
};
</script>
