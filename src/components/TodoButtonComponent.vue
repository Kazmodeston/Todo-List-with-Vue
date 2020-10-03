<template>
<div>
    <input type="text" id="todo-text" v-model="form.message" @keyup.enter="send" placeholder="Add your todo" />
</div>
</template>

<script>
export default {
    props: [
        todoMessage
    ],
    data() {
        return {

        }
    },
    methods: {
        send() {

            if (this.form.message.length != 0) {
                this.todoMessage.push({
                    "message": this.form.message,
                    "bool": this.form.bool
                })
                this.form.message = ""
            }
        }
    }
}
</script>

<style scoped>

</style>
