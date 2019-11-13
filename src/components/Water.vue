<template>
    <v-container fluid>
      <v-row align="center">
        <v-col class="d-flex flex-column mx-auto" cols="12" lg="12" sm="6">
            <v-container class="py-0" fluid>
                <h2 v-bind:style="headerStyle">
                    Water Intake
                    <v-icon class="heart mb-1">mdi-cup-water</v-icon>
                </h2>
                <div class="d-flex align-center justify-center my-4 flex-column">
                    <ul class="list-group d-flex justify-center align-center px-0">
                        <li 
                            v-for="(option, index) in options" 
                            :key="index"
                            class="mx-2"
                        >
                            <button v-on:click="feelings(option)" class="d-flex flex-column justify-center align-center">
                                <img src="drop.svg" height="50" class="water" />
                                {{ option }}
                            </button>
                        </li>
                    </ul>
                    <div class="my-5">
                        <p id="waterResult"></p>
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
            options: [1,2,3,4,5,6,7,8]
        }
    },
    methods: {
        feelings: function (x) {
            if (x === 1) {
                document.getElementById('waterResult').innerHTML = `${x} glass so far. Start drinking!`
            }
            if (x >= 2 && x < 5) {
                document.getElementById('waterResult').innerHTML = `${x} glasses so far. Keep going!`
            }
            if (x === 5) {
                document.getElementById('waterResult').innerHTML = `${x} glasses so far. Only 3 more and you've reached your daily goal :)`
            }
            if (x >= 6 && x <= 7) {
                document.getElementById('waterResult').innerHTML = `${x} glasses so far. Almost there.`
            }
            if (x === 8) {
                document.getElementById('waterResult').innerHTML = `${x} glasses! You've officially reached your goal. Keep going, or switch to wine - you've earned it.`
            }
        }
    }
}
</script>

<style scoped>
li {
    list-style-type: none;
}
img.water {
    transition:0.5s;
}
img.water:hover {
    height: 60px;   
}
#waterResult {
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

<!-- <div>Icons made by <a href="https://www.flaticon.com/authors/vectors-market" title="Vectors Market">Vectors Market</a> from <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a></div> -->