<template>
  <div id="app">
    <header>
      <h1>My Music</h1>
    </header>
    <main>
      <section class="player">
        <h2 class="song-title">{{current.title}} - <span>{{current.artist}}</span></h2>
        <div class="controls">
           <button class="prev" @click="prev">Prev</button>
           <button class="play" v-if="!isPlaying" @click="play">Play</button>
           <button class="pause" v-else @click="pause">Pause</button>
           <button class="next" @click="next">Next</button>
        </div>
      </section>
      <section class="playlist">
        <h3>The Playlist</h3>
        <button v-for="song in songs" :key="song.src" @click="play(song)" :class="(song.src == current.src) ? 'song playing' :'song'">{{song.title}} - {{song.artist}}</button>
      </section>
    </main>
  </div>
</template>

<script>


export default {
  name: 'App',
  data () {
    return {
      current: {
       
      },
      index: 0,
      isPlaying: false,
      songs: [
        {
        title: 'Gotay',
        artist: 'Nessi',
        src: require('./assets/Gotay_El_Autentiko_Ft_Nesi_-_Soltero.mp3')
      },
      {
        title: 'Rolling',
        artist: 'Blackouts',
        src: require('./assets/Rolling_Blackouts_Coastal_Fever_-_Tidal_River.mp3')
      }
      ],
      player: new Audio()
    }
  },
  methods: {
    play (song) {
      if (typeof song.src != "undefined") {
        this.current = song;

        this.player.src = this.current.src;
      }
      this.player.play();
      this.player.addEventListener('ended', function () {
        this.index++;
        if (this.index > this.songs.index - 1) {
        this.index = 0;
      }

      this.current = this.songs[this.index];

      this.play(this.current);


      }.bind(this));

    },
    pause () {
      this.player.pause();
      this.isPlaying = false;
    },
    prev () {
      this.index--;
      if (this.index < 0) {
        this.index = this.songs.length - 1;
      }
      
      this.current = this.songs[this.index];

      this.play(this.current);

    },
    next () {
      this.index++;
      if (this.index > this.songs.index - 1) {
        this.index = 0;
      }

      this.current = this.songs[this.index];

      this.play(this.current);
    }

  },
  //Lifecycle methods
  created () {
    this.current = this.songs[this.index];
    this.player.src = this.current.src;
    // this.player.play();
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: sana-serif;
}

header {
  display:flex;
  justify-content: center;
  align-items: center;
  padding: 15px;
  background: #212121;
  color: #fff;
}

main {
  width: 100%;
  max-width: auto;

}
</style>
