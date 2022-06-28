<template>
  <div id="app">
    <header>
      <h1>My Music</h1>
    </header>
    <main>
      <section class="player">
        <h2 class="song-title">{{current.title}}</h2>
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
        title: 'SONG TITLE'
      },
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
      ]
    }
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
</style>
