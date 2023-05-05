<script>
    export default{
    
        data() {
            return {
                min: 1,
                max: 100,
                answer: 65,
                hyphen: "-",
                guess: "",
                message: "猜一個數字",
                wrong: "猜錯了，再猜一次",
                right: "恭喜猜對了",
                wrongFormat: "請輸入範圍內的數字", 
                response: true

            }
        },
        methods: {
            responseNum(){
                if(this.guess > this.max || this.guess < this.min){
                    this.message = this.wrongFormat
                    this.guess = null
                    return
                }

                if(this.guess > this.answer){
                    this.max = this.guess;
                    this.message = this.wrong;
                    this.max = this.guess;
                    this.guess = null
                    
                }

                if(this.guess < this.answer){
                    this.min = this.guess;
                    this.message = this.wrong;
                    this.min = this.guess;
                    this.guess = null
                       
                } 

                if(this.guess == this.answer){
                    this.message = null
                    this.min = null
                    this.max = null
                    this.hyphen = this.right
                    
                }
                
            }
        },
        mounted() {
            
        },
    
    
    
    }
</script>

<template>
    <div class="area1">
        <div class="number-area">
            <h5 class="mt-4">{{ message }}</h5>
        </div>
        <div class="number-area">
            <h1>{{ min }}</h1>
            <h1>{{ hyphen }}</h1>
            <h1>{{ max }}</h1>
        </div>

        <div class="number-area" >
            <input type="number" v-model="guess"> 
        </div>
        <!-- <div class="number-area" >
            <input type="number" id="maxInput" v-model="max"> 
        </div> -->

        <div class="number-area">
            <button type="button" class="btn btn-dark" v-on:click="responseNum">Response</button>
        </div>
    </div>
</template>

<style lang="scss" scoped>
    .area1 {
        width: 300px;
        height: 300px;
        margin: auto;
        margin-top: 100px;   
        background-color: cadetblue;
        border-radius: 3%;

        h3 {
            margin-top: 20px;
            text-align: center;
        }

        .number-area {
            margin-bottom: 20px;
            display: flex;
            justify-content: space-evenly;

            h1 {
                text-align: center;
            }

            input {
                width: 200px;
                height: 30px;
                font-size: 20px;
                border-radius:5px;
                border:1px
                solid #ccc;
                text-align: center;
            }
        }

        .number {
            text-align: center;
        }
    }
</style>