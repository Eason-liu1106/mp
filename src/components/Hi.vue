<template>
    <div id="jhi" href="/#/url" >
        <h1>{{msg}}</h1>
        <h1 @click="click1">{{msg1}}</h1>
        <h1>{{msg2}}</h1>
        <input  type="button" @click="sendAll">
        <input type="text" v-model="abc">
    </div>
</template>

<script>
import axios from "axios"

    export default {
        props: {
            msg: ''
        },
        data () {
            return {
                msg1: "我是大傻逼",
                msg2: "msg2",
                abc: ''
            }
        },
        created () {
            console.log("created");
            var ws = this.ws = new WebSocket("ws://127.0.0.1:8002/api/ws/asset");
            ws.onopen = function()
            {
                console.log("open");
                ws.send("hello");
            };
            ws.onmessage = (evt) =>
            {
                console.log(evt.data)
                this.abc = evt.data
            };
            ws.onclose = function(evt)
            {
                console.log("WebSocketClosed!");
            };
            ws.onerror = function(evt)
            {
                console.log("WebSocketError!");
            };

        },
        destroyed () {

        },
        methods: {
            click1 () {
                console.log(1);
            },
            sendAll () {
                axios.get('/api/ws/sendAll',{
                    params:{
                        message:'大家滴滴滴滴'
                    }
                })
                    .then(function (res) {
                        this.msg2 = res.msg
                        console.log(res);
                    })
                    .catch(function () {

                    })
            }
        }
    }
</script>

<style scoped>

</style>