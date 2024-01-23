<template>
    <div id="bg_load">
        <video src="../assets/Background1.mp4" autoplay muted loop></video>
        <img id="logo" src="../assets/Affilium2logo.png" alt="">
        <i v-for="index in 100" :key="index" class="uil uil-circle star"></i>
    </div>
    <!-- <div id="main">
        <form action="">

        </form>
    </div> -->
</template>

<script>
import { gsap } from "gsap";

const colors = ["rgb(19, 85, 161)", "rgb(109, 15, 163)", "rgb(254, 250, 255)"];

function selectRandom(array) {
    return array[Math.floor(Math.random() * array.length)];
}

export default {
    name: 'Loading',
    mounted() {
        gsap.fromTo('#logo',
            {
                opacity: 0,
                
            },
            {
                ease: "bounce.out",
                duration: 1,
                opacity: 1,
                scale: 2,
                delay: 0.1
            });
        
        const stars = document.querySelectorAll('.star');
            
        gsap.to(stars, {
            duration: 2.5,
            opacity: 0,
            x: () => Math.random() * window.innerWidth - window.innerWidth / 2,
            y: () => Math.random() * window.innerHeight - window.innerHeight / 2,
            rotation: () => Math.random() * 360,
            scale: 1,
            color: () => selectRandom(colors),
        });
    }
}

</script>

<style>

i {
    font-size: 35px;
    color: white;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%,-50%);
}
#bg_load {
    position: relative;
    width: 100vw;
    height: 100vh;
    overflow: hidden;
    /* background-color: black; */
}
video {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    z-index: -1;
}
img {
    width: 300px;
    z-index: 1;
}
#logo {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%,-50%);

}
</style>