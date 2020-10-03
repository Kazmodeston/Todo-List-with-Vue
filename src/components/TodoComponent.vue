<template>
<div id="todo-list-holder">
    <div class="row">
        <div class="col-sm-12">
            <input type="text" id="todo-text" v-model="form.message" @keyup.enter="send" placeholder="Add your todo" />
            <ul class="list-group">

                <li v-for="todoMessages in todoMessage" :key="todoMessages.index" class="list-group-item">

                    <div class="row">

                        <div class="col-sm-12">
                            <div class="float-left">
                                <input type="checkbox" v-model="todoMessages.bool" />&nbsp; &nbsp;<span :class="{ textStrike : todoMessages.bool }">{{todoMessages.message}}</span>
                            </div>

                            <div class=" float-right">
                                <!--
                                <span id="edit-fontawesome"  @click="mySelected(todoMessages)">
                                    <i class="far fa-edit"></i>
                                </span> &nbsp;
                                -->
                                <span id="delete-fontawesome">
                                    <i class="far fa-trash-alt" @click="remove(todoMessages)"></i>
                                </span>
                            </div>
                        </div>

                    </div>

                </li>
            </ul>
        </div>
    </div>
</div>
</template>

<script>
export default {
    data() {
        return {
            form: {
                message: "",
                bool: false
            },
            todoMessage: []
        }
    },
    methods: {
        send() {
            if (this.todoMessage.length == 5) {
                swal({
                    title: "Information!",
                    text: "You can't add more than 5 Todo List!",
                    icon: "warning",
                });
                return
            }
            if (this.form.message.length != 0) {
                this.todoMessage.push({
                    "message": this.form.message,
                    "bool": this.form.bool
                })
                this.form.message = ""
            }
        },
        remove(todoMessages) {
            let index = this.todoMessage.indexOf(todoMessages)
            this.todoMessage.splice(index, 1)
        },

    }
}
</script>

<style scoped>
#todo-list-holder {
    border: 1px solid #DDD;
    overflow-y: scroll;
    height: 500px;
    background-color: white;
    overflow-x: hidden;
}

#todo-text {
    font-size: 18px;
    padding: 10px 5px;
    width: 469px;
    /*border: 1px solid #DDD;*/
    border: none;
}

#edit-fontawesome {
    font-size: 20px;
    color: Dodgerblue;
    cursor: pointer;
}

#delete-fontawesome {
    font-size: 20px;
    color: red;
    cursor: pointer;
}

.textStrike {
    text-decoration: line-through;
}
</style>
