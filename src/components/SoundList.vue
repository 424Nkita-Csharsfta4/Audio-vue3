<template>
    <div v-if="!isPlayerVisible">
        <div class="text-300 font-bold text-center text-3xl mb-7 mt-3">
           Топ 4 фонка
        </div>
        <div
            v-for="(song, songIndex) in list" v-bind:key="song.id"
            class="flex flex-row justify-between mb-4 cursor-pointer"
            v-on:click="playSong(songIndex)"
        >
            <div>
                <span class="text-red-300">{{ song.name }}</span>
                <br />
                <span class="text-200 text-xs">
                    {{ song.artistName }} - 
                    <span class="text-gray-400"> {{ song.albumName }} ({{ song.year }})</span>
                </span>
            </div>
            <div>
                <img
                    class="max-h-12 rounded"
                    v-bind:src="song.src"
                />
            </div>
        </div>
    </div>
    <div v-if="isPlayerVisible">
        <SoundPlayers 
            v-bind:song="list[currentSongIndex]"
            @goback="isPlayerVisible = !isPlayerVisible"
            @next="playNext"
            @previous="playPrevious"
        />
    </div>
</template>

<script>
import SoundPlayers from '../components/SoundPlayer.vue';

export default {
    data () {
        return {
            isPlayerVisible: false,
            currentSongIndex: 0,
            list: [
                {
                    id: 1,
                    name: 'IMMACULATE (Sped Up)',
                    artistName: 'VISXGE',
                    albumName: 'IMMACULATE',
                    year: 2022,
                    src: `https://sun9-78.userapi.com/impf/IjSDXV-Buk4PwOy-X2cYKJ0kIXeDc3mi6MtLJg/PlbRDd49o-4.jpg?size=400x0&quality=90&sign=29f01123df7a1845770b071f77166d6b`,
                    songSrc: `https://s123.convertio.me/p/r8tnRkPHpcMBqpZPF8d-UQ/bd7ff6ab0a94bb58c7dfc3c2278d4852/VISXGE-IMMACULATE-_Sped-Up_.mp3`
                },
                {
                    id: 2,
                    name: 'Тесно',
                    artistName: 'Aarne, BUSHIDO ZHO, ANIKV',
                    albumName: 'Arne',
                    year: 2022,
                    src: `https://sun9-87.userapi.com/impf/gK5aIQwj7783jyST7TeRP09hxEXcnGQf92GbiQ/kiN_Al6AAB8.jpg?size=400x0&quality=90&sign=64173d6cb22b9ada5643e963186d8ae1`,
                    songSrc: `https://s161.convertio.me/p/KoHPNt6TzEu8teU1Hwm6-g/bd7ff6ab0a94bb58c7dfc3c2278d4852/Aarne_-BUSHIDO-ZHO_-ANIKV-Тесно.mp3`
                },
                {
                    id: 3,
                    name: 'FIGHT CLUB',
                    artistName: 'MoonDeity, EL$E',
                    albumName: 'EL$E',
                    year: 2021,
                    src: `https://sun9-36.userapi.com/impf/q24oV_5DJd89CowrVSc-zmzkixCt8Py6tDkrfA/kbPL4ZnwYEM.jpg?size=400x0&quality=90&sign=d0745f2f32777ca6c84bed4318a8257e`,
                    songSrc: `https://s170.convertio.me/p/P9UUdxcOfFmYuKX4jNzAmQ/bd7ff6ab0a94bb58c7dfc3c2278d4852/MoonDeity_-EL_E-FIGHT-CLUB.mp3`
                },
                {
                    id: 4,
                    name: 'WAKE UP!',
                    artistName: ' MoonDeity',
                    albumName: ' MoonDeity',
                    year: 2019,
                    src: `https://sun9-84.userapi.com/impf/ukvvdP-d64zqYMrWc1mReO-rMb9rfkQY2d9ESg/X8HSeLIs3tQ.jpg?size=400x0&quality=90&sign=a80a30bc4ab4d50826ad02814980f54e`,
                    songSrc: `https://s134.convertio.me/p/7OcWnxk_Dr-mDe_3C9S9LA/bd7ff6ab0a94bb58c7dfc3c2278d4852/MoonDeity-WAKE-UP__1.mp3`
                }
            ]
        }
    },
    methods: {
        playSong (index) {
            this.currentSongIndex = index;
            this.isPlayerVisible = true;
        },
        playNext () {
            if (this.currentSongIndex < this.list.length - 1) {
                this.currentSongIndex += 1;
            } else {
                this.currentSongIndex = 0;
            }
        },
        playPrevious () {
            if (this.currentSongIndex != 0) {
                this.currentSongIndex -= 1;
            } else {
                this.currentSongIndex = this.list.length - 1;
            }
        } 
    },
    components: {
        SoundPlayers
    }
}
</script>