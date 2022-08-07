<template>
    <section class="gallery">
        <div class="photoset -square -portrait">
            <a v-for="image in images" :href="image" target="_blank" class="photo" :style="`background-image:url(${image})`" :key="image"></a>
        </div>
    </section>
</template>

<script>
    import axios from 'axios'

    export default{
        name:'BodyComponent',
        data(){
            return{
                images:[],
            }
        },
        methods:{

        },
        async created(){
            var res = await axios.get('http://shibe.online/api/shibes?count=1000');
            this.images = res.data;
        }
    }
</script>

<style scoped lang="scss">
    section{
        width: 100%;
        display: flex;
        justify-content: center;
    }

    div.photoset {
        padding: 2px;
        background-color: #ffffff;
        width: 80%;
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        .photo {
            position: relative;
            flex-grow: 1; //They will fill space but actually want to take up the smallest space possible doing it, so you just need to stop it getting too small with min-width (otherwise they all bunch on the same line)
            min-width: calc(100% / 3); //This is the maximum number (3) in a row bit
            background-size: cover;
            background-position: center;
            
            @media screen and (max-width: 700px) {
                min-width: calc(100% / 2); //As simple as this for responsiveness without a delay you would get with JavaScript
            }
            @media screen and (max-width: 460px) {
                min-width: 100%;
            }
            &:after {
                //Aspect Ratio
                padding-top: 83.33333%; //For 5:6 height to width ratio
                display: block;
                content: "";
            }
            &:before {
                //Gaps
                z-index: 2;
                position: absolute;
                content: "";
                top: 0px;
                right: 0px;
                bottom: 0px;
                left: 0px;
                box-shadow: inset 0 0 0 2px #ffffff; //Cheaty way to make it look like there are gaps 😜
            }
            &:nth-child(1) {
                //Make first image big
                width: 100%;
            }
        }

        &.square .photo:after {
            padding-top: 100%;
        }
        &.portrait .photo:after {
            padding-top: 120%;
        }
    }

    body {
        background-color: #ece9e2;
        overflow-y: scroll;
        display: flex;
        flex-direction: column;
        align-items: center;
        margin: 10px;
    }

</style>