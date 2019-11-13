<template>
    <v-container fluid>
      <v-row align="center">
        <v-col class="d-flex flex-column mx-auto" cols="12" lg="12" sm="6">
            <v-container class="py-0" fluid>
                <h2 v-bind:style="headerStyle">
                    How are you?
                    <v-icon class="heart mb-1">mdi-heart-outline</v-icon>
                </h2>
                <div class="d-flex align-center justify-center my-4 flex-column">
                    <ul class="list-group d-flex justify-center align-center px-0">
                        <li 
                            v-for="(option, index) in options" 
                            :key="index"
                            class="mx-5"
                        >
                            <button v-on:click="feelings(option.title)" class="d-flex flex-column justify-center align-center">
                                <img :src="option.image" height="50" class="emotion" />
                                {{ option.title }}
                            </button>
                        </li>
                    </ul>
                    <div class="my-5">
                        <p id="feelingsResult"></p>
                    </div>
                </div>
            </v-container>
        </v-col>
      </v-row>
    </v-container>
</template>

<script>
export default {
    data() {
        return{
            selected: '',
            headerStyle: [
                {
                    textTransform: 'uppercase',
                    fontWeight: 'thin',
                    color:'#f15e53',
                    letterSpacing: '0.5px',
                    margin: '0 auto'
                }
            ],
            options: [
                {
                    title: "mad",
                    image: "././angry.svg"
                },
                {
                    title: "sad",
                    image: "././sad.svg" 
                },
                {
                    title: "neutral",
                    image: "././neutral.svg" 
                },
                {
                    title: "happy",
                    image: "././happiness.svg" 
                },
                {
                    title: "great",
                    image: "././happy.svg" 
                }
            ]
        }
    },
    methods: {
        feelings: function (x) {
            if (x === 'mad') {
                document.getElementById('feelingsResult').innerHTML = `why do you feel ${x}? Try writing down your feelings.`
            }
            if (x === 'sad') {
                document.getElementById('feelingsResult').innerHTML = `What made you feel ${x}? Take 10 minutes to de-stress - try going for a walk.`
            }
            if (x === 'neutral') {
                document.getElementById('feelingsResult').innerHTML = `Lets bump that mood up from ${x} to great!`
            }
            if (x === 'happy') {
                document.getElementById('feelingsResult').innerHTML = `Right on! Write down what's keeping you ${x} so you can reflect on it later`
            }
            if (x === 'great') {
                document.getElementById('feelingsResult').innerHTML = `Sweet! Keep having yourself a ${x} day :)`
            }
        }
    }
}
</script>

<style scoped>
li {
    list-style-type: none;
}
img.emotion {
    transition:0.5s;
}
img.emotion:hover {
    height: 60px;    
}
#feelingsResult {
    font-size: 16px;
    text-transform: lowercase;
    line-height:25px;
}
.v-icon {
    color:#f15e53;
}
.v-icon:not(.heart) {
    font-size: 40px;
    margin:0 20px;
}
</style>
