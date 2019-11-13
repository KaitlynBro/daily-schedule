<template>
    <v-container fluid>
      <v-row align="center">
        <v-col class="d-flex flex-column mx-auto" cols="12" lg="12" sm="6">
            <v-container class="py-0" fluid>
                <h2 v-bind:style="headerStyle">
                    {{ header }}
                </h2>
                <div class="d-flex align-center justify-center my-4 flex-column">
                    <ul class="list-group d-flex justify-center align-center px-0">
                        <li 
                            v-for="(option, index) in options" 
                            :key="index"
                            class="mx-2"
                        >
                            <button v-on:click="feelings(option.title)" class="d-flex flex-column justify-center align-center">
                                <img :src="option.image" height="50" class="water" />
                                <!-- <div>Icons made by <a href="https://www.flaticon.com/authors/vectors-market" title="Vectors Market">Vectors Market</a> from <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a></div> -->
                                {{ option.title }}
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