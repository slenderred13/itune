<template>
<div>
    <img src="https://seeklogo.com/images/I/iTunes-logo-84CDFAEE47-seeklogo.com.png" alt="" height="150px" width="250px" class="img-fluid mx-auto rounded-circle" />
    <br />
    <br />
    <div class="row">
        <div class="col">
        </div>
        <div class="col">
            <input class="form-control ds-input " type=" text" v-model="keyword" placeholder="Insert your music" />
            <br />
            <button @click="searchData" class="btn btn-primary">Search</button>
            <!--{{resultData}} -->
        </div>
        <div class="col">
        </div>
    </div>
    <br />
    <br />
    <div class="row">
        <div class="col-sm"></div>
        <div class="col-auto">
            <b-card-group columns>
                <div v-for="data in resultData" :key="data.trackId">
                    <b-card :title="data.title" :img-src="data.artworkUrl100" img-alt="Image" img-top tag="article" style="max-width: 22rem;" class="mb-2">
                        <b-card-text>{{ data.trackName }}</b-card-text>
                        <b-card-text>{{ data.artistName }}</b-card-text>
                        <audio controls >
                            <source :src="data.previewUrl" type="audio/mpeg"/>
                        </audio>
                        <b-button :href="data.trackViewUrl" variant="primary">Play</b-button>
                    </b-card>
                </div>
            </b-card-group>
        </div>
        <div class="col-sm"></div>
    </div>
</div>
</template>

<script>
import axios from "axios";
export default {
    data() {
        return {
            resultData: null,
            keyword: "",
        };
    },
    methods: {
        searchData() {
            axios
                .get(
                    "https://itunes.apple.com/search?term=" + this.keyword + "&limit=15"
                )
                .then((response) => {
                    this.resultData = response.data.results;
                })
                .catch((err) => {
                    console.log(err);
                });
        },
    },
};
</script>

<style>
.card {
    background-image: url('https://i.pinimg.com/originals/f4/52/a2/f452a2f4b634b3011e065da8eaf0a5c3.gif');
}
</style>
