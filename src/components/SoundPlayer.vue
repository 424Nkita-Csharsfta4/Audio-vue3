<template>
    <audio v-bind:src="song.songSrc" preload="auto" autoplay ref="audioPlayer" />
    <div class="text-white">
        <div class="flex flex-row justify-between">
            <button v-on:click="goback"><i class="bi bi-arrow-left-circle"></i></button>
            <div class="text-yellow-300 font-bold text-1xl">Аудио плеер</div>
        </div>
        <div>
            <img class="rounded mt-8 mb-4" v-bind:src="song.src" />
            <div class="text-center">
                <p class="text-yellow-300 font-bold">{{ song.name }}</p>
                <p class="text-gray-200">{{ song.artistName }} - {{ song.albumName }}</p>
                <p class="text-gray-400">{{ song.year }}</p>
            </div>
        </div>
        <div class="grid grid-cols-3 mt-10">
            <div class="flex items-center justify-center">
                <button v-on:click="previous"><i class="bi bi-arrow-left-square-fill"></i></button>
            </div>
            <div class="flex items-center justify-center">
                <button
                    class="rounded-full bg-yellow-300 h-24 w-24 text-black font-bold"
                    v-on:click="togglePlay"
                >
                    {{ isPlaying ? 'Пауза' : 'Продолжить' }}
                </button>
            </div>
            <div class="flex items-center justify-center">
                <button v-on:click="next"><i class="bi bi-arrow-right-square-fill"></i></button>
            </div>
        </div>
    </div>
</template>
<style>
i{
  border-radius: 20px;
}
</style>
<script>
export default {
    data () {
        return {
            isPlaying: true
        }
    },
    name: 'SongPlayer',
    props: {
        song: {
            id: Number,
            name: String,
            artistName: String,
            albumName: String,
            year: Number,
            src: String,
            songSrc: String
        },
    },
    emits: ['goback', 'next', 'previous'],
    methods: {
        goback () {
            this.$emit('goback');
        },
        togglePlay () {
            if (this.isPlaying) {
                this.$refs.audioPlayer.pause();
            } else {
                this.$refs.audioPlayer.play();
            }
            this.isPlaying = !this.isPlaying;
        },
        next () {
            this.$emit('next');
        },
        previous () {
            this.$emit('previous');
        }
    }
}
</script>