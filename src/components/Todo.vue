<template>
    <div class="todo-wrapper">
        <div class="row">
            <div class="col-md-12">
                <div class="well">
                    <h2 v-bind:style="headerStyle">Todo</h2>
                    <form v-on:submit.prevent="add">
                        <div class="form-group" v-bind:style="toDo">
                            <input type="text" v-model="input" v-bind:style="inputStyle" class="form-control" placeholder="add item" required />
                            <button 
                                type="submit" 
                                class="btn btn-default add"
                                @keyup.enter="add()"
                                v-bind:style="buttonStyle"
                                >
                            add</button>
                        </div>
                    </form>
                </div>
            </div>
        </div>
        <div class="row" v-bind:style="scrollStyle">
            <div class="listed" v-bind:style="{ width: '100%' }">
                <ul class="list-group" v-bind:style="listGroup">
                    <li 
                        v-for="(todo, index) in todos" 
                        :key="index" 
                        v-bind:style="listStyle"
                    >
                        <span v-bind:style="{ 'margin-left': '5px' }">{{ todo}}</span>
                        <button 
                            v-on:click="todos.splice(index, 1)"
                            class="btn btn-default done"
                            v-bind:style="done"
                        >
                        </button>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Todo",
        data () {
            return {
                todos: [],
                input: "",
                headerStyle: [
                    {
                        textTransform: 'uppercase',
                        padding: '10px 0',
                        fontWeight: 'thin',
                        color:'#f15e53',
                        letterSpacing: '0.5px'
                    }
                ],
                toDo: [
                    {
                        width: '80%',
                        margin: '0 auto',
                        padding: '10px 0',
                        display: 'flex',
                        flexDirection: 'row',
                        justifyContent: 'center',
                        alignItems: 'center'
                    }
                ],
                inputStyle: [
                    {
                        borderBottom:'1px solid black',
                        width: '90%',
                        paddingLeft: '8px'
                    }
                ],
                buttonStyle: [
                    {
                        width: '10%',
                        border: '1px solid black',
                        transition: '0.5s',
                        position: 'relative'
                    }
                ],
                listGroup: [
                    {
                        padding: '20px',
                        textAlign: 'left',
                        listStyleType: 'none',
                        lineHeight:'3',
                        display: 'flex',
                        flexWrap: 'wrap',
                        width: '90%',
                        margin: '0 auto',
                        position: 'relative'
                    }
                ],
                scrollStyle: [
                    {
                        maxHeight: '250px',
                        width: '95%',
                        overflow: 'scroll'
                    }
                ],
                done: [
                    {
                        border: '1px solid black',
                        borderRadius: '100px',
                        margin: '0 10px',
                        position: 'relative',
                        padding: '10px',
                        transition: 'all 1s'
                    }
                ],
                listStyle: [
                    {
                        width: '45%',
                        display: 'flex',
                        alignItems: 'center',
                        justifyContent: 'space-between',
                        flexDirection: 'row',
                        backgroundColor: '#fdc0b0',
                        padding: '5px',
                        boxSizing: 'border-box',
                        margin: '5px',
                        transition: '1s'
                    }
                ]
            }
        },
        methods: {
            add() {
                this.todos.push(this.input);
                this.input = "";
            }
        }
    }
</script>

<style lang="scss" scoped>
@import "../styles/variables.scss";

button {
    &:hover {
        background-color: $pinkLight;
    }
}
.done {
    position: relative;
}
.done:after {
    content: "+";
    position: absolute;
    top: -15px;
    left: 50%;
    font-size: 16px;
    font-weight: bold;
    transform: translate(-50%);
    padding: 0 3px;
    box-sizing: content-box;
    transition: 0.5s;
}

.list-group:after{
    position: fixed;
    content: "scroll for more items";
    right: 20px;
    transform: rotate(90deg);
    font-size: 19px;
    top: 35%;
}

button.done:hover {
    padding:13px !important;
    background-color:$pinkDark;
    &:after {
        top: -10px;
        content: "✓";
    }
}
</style>