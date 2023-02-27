<template>
    <div>
        <div class="bg-image hero__height">
            <div class="container">
                <div class="row">
                    <div class="col-xxl-6 col-xl-6 col-lg-6 col-md-8 col-sm-8">
                        <div class="hero__content">
                            <h2 class="hero__title">
                                <span
                                    class="fw-300"
                                    @mouseenter="onMounseEnterEvt"
                                    @mouseleave="onMouseLeaveEvt"
                                    >Happy Birthday, Maxoxoxo 🥳</span
                                >
                                <br />
                                <button
                                    class="btn btn-dark"
                                    @click="onBtnClick()"
                                >
                                    Click me 🎁
                                </button>
                            </h2>
                        </div>
                    </div>
                    <div class="col-xxl-6 col-xl-6 col-lg-6 col-md-8 col-sm-8">
                        <img
                            src="../assets/cat1.png"
                            alt=""
                            class="banner_cat"
                        />
                    </div>
                </div>
            </div>

            <!-- <button class="btn btn-primary" @click="playSong">play</button> -->
        </div>
        <div>
            <div id="cat-row" class="row bg2-image">
                <h4 id="message">Dearest Max, <br><br> Many Many Happy returns of the day.<br>
                Although we have never met in real life, don't know how each other are or will be when we <br>
                meet.. but I want you to know.. whatever time I've spent talking with you.. that has been <br>
                the best time I have ever had in this world. <br>
                Thank you Maxo monkey 🐒, for always being there for me.. and filling my life with joy and happiness! ✨ <br>
                May God bless you exceedingly and abundantly more in what’s in store than he ever has before. ❤️ 
                <br> <br>
                Yours truly, <br>
                Anuj
                </h4>
                <div class="col-md-3 cat-column">
                    <img
                        src="../assets/sub_cat1.png"
                        alt=""
                        class="banner2_cat1"
                    />
                </div>
                <div class="col-md-3 cat-column">
                    <img
                        src="../assets/sub_cat2.png"
                        alt=""
                        class="banner2_cat1"
                    />
                </div>
                <div class="col-md-3 cat-column">
                    <img
                        src="../assets/sub_cat3.png"
                        alt=""
                        class="banner2_cat1"
                    />
                </div>
                <div class="col-md-3 cat-column">
                    <img
                        src="../assets/sub_cat4.png"
                        alt=""
                        class="banner2_cat1"
                    />
                </div>
            </div>
        </div>
    </div>
</template>
<script>
const song = require("@/assets/song.mp3");
export default {
    data: () => ({
        isSongPlaying: false,
        message: ""
    }),
    methods: {
        startConfetti() {
            this.$confetti.start();
            this.$confetti.update({
                particles: [
                    {
                        type: "heart",
                    },
                    {
                        type: "circle",
                    },
                ],
                defaultColors: ["red", "pink", "#ba0000"],
            });
        },

        stopConfetti() {
            this.$confetti.stop();
        },

        onMouseLeaveEvt() {
            this.stopConfetti();
        },

        onMounseEnterEvt() {
            // this.startConfetti()
        },
        playSong() {
            // this.startConfetti()
            let audio = new Audio(song);

            audio.autoplay = true;
            audio
                .play()
                .then((response) => {
                    console.log(response);
                })
                .catch((error) => {
                    console.log(error);
                });
        },

        onBtnClick() {
            this.startConfetti();
            if (!this.isSongPlaying) {
                this.playSong();
                this.isSongPlaying = true;
            }
        },
    },

    mounted() {
      
    },
};
</script>

<style scoped>
.bg-image {
    height: 50%;
    background-repeat: no-repeat;
    position: relative;
    background: url("../assets/bg.png");
    background-size: cover;
    /* color: white; */
}

.bg2-image {
    height: 119vh;
    width: 100%;
    background-repeat: no-repeat;
    position: relative;
    background: url("../assets/bg2.png");
    background-size: cover;
    /* color: white; */
}

.hero__height {
    height: 100vh;
}

#message {
    position: absolute;
    top: 200px;
    padding-left: 200px;
    font-family: 'Oleo Script Swash Caps';
}

.banner_cat {
    height: 80vh;
}

.banner2_cat1 {
    text-align: center;
    height: 40%;
    position: relative;
    bottom: 0;
    animation: catMove 5s infinite;
}

.cat-column {
    display: flex;
    flex-direction: column-reverse;
}

.hero__content {
    position: relative;
    z-index: 1;
}

.hero__content p {
    padding-right: 100px;
    margin-bottom: 40px;
    font-size: 16px;
}

.hero__title {
    font-size: 60px;
    font-weight: 300;
    margin-top: 250px;
    margin-bottom: 17px;
}

@keyframes catMove {
    0% {
        left: 0px;
    }
    25% {
        left: 10px;
    }
    75% {
        left: 15px;
    }
    100% {
        left: 0px;
    }
}
</style>