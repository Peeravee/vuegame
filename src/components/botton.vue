<template>
  <div>
    <div class="row">
      <div class="col-sm">
        <p style="font-size: 150%">{{aplayer.name}}</p>
        <p>
          <img v-bind:style="{width: aplayer.hp + 'px'}" :src="hp1" alt height="20px" />
        </p>
        <p style="font-size: 150%">{{thp}}{{aplayer.hp}}</p>
        <p>
          <img style="width:50%" :src="aplayer.image" />
        </p>
      </div>
      <!-- Botton -->
      <div class="col-sm">
        <div class="row">
          <div class="col">
            <div class="btn-group" role="group" aria-label="Basic example">
    <button v-bind:disabled="end" class="btn btn-primary" @click="start()">Start</button>
    <button v-bind:disabled="end" class="btn btn-light" @click="attack()">Attack</button>
    <button v-bind:disabled="end" class="btn btn-danger" @click="special()">SpecialAttack</button>
    <button class="btn btn-success" @click="reset()">Restart</button>
</div>
          </div>
          <br /> 
          <!-- VS -->
          <center><img
            src="https://media1.giphy.com/media/Q8TlZx35X6xDdJidvT/source.gif"
            width="80%"
          />
          </center>
         </div>
        <div class="row">
          <div class="col-sm"></div>
          <div class="col-sm">
            <div id="score">
              <!-- WIN -->
              <div v-if="amonster.hp <= 0"><img
            src="https://media3.giphy.com/media/jsGz81YPCgw9YSliV0/giphy.gif"
            width="100%"
          /></div>
              <!-- LOST -->
              <div v-else-if="aplayer.hp <= 0"><img
            src="https://1.bp.blogspot.com/-bSl9eHawN-A/W6uUEP4EHVI/AAAAAAAwLiI/jjtXZMGvtkwB1kQH9wqrI3T2Soy3JTBlQCLcBGAs/s1600/AW1880226_11.gif"
            width="150%"
          /></div>
            </div>
          </div>
          <div class="col-sm"></div>
        </div>
      </div>
      <div class="col-sm">
        <p style="font-size: 150%">{{amonster.name}}</p>
        <p>
          <img v-bind:style="{width: amonster.hp + 'px'}" :src="hp2" alt height="15px" />
        </p>
        <p style="font-size: 150%">{{thp}}{{amonster.hp}}</p>
        <p>
          <img style="width:50%" :src="amonster.image" />
        </p>
      </div>
    </div>
    
      
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      thp: "HP:",
      end: false,
      hp2:
        "https://img.pngio.com/health-bar-png-100-images-in-collection-page-3-health-bar-png-1200_900.png",
      hp1:
        "https://img.pngio.com/health-bar-png-pictures-trzcacakrs-health-bar-png-1190_1120.png",
      aplayer: { name: "", hp: 1, image: "", hp1: "" },
      player: [
        
        {
          name: "Dhalsim",
          hp: 330,
          image:
            "https://i.pinimg.com/originals/c0/53/f2/c053f2bce4d2375fee8741acfb35d44d.gif",
        },
        {
          name: "Vega",
          hp: 250,
          image:
            "https://www.fightersgeneration.com/np5/char/ssf2hd/vega-hdstance.gif",
        },
        {
          name: "Dee Jay",
          hp: 330,
          image:
            "https://www.fightersgeneration.com/np5/char/ssf2hd/deejay-hdstance.gif",
        },
        {
          name: "Zangief",
          hp: 400,
          image: "https://giffiles.alphacoders.com/131/13197.gif",
        },
        {
          name: "Ken",
          hp: 450,
          image: "https://giffiles.alphacoders.com/131/13192.gif",
        },
        {
          name: "M. Bison",
          hp: 500,
          image:
            "https://www.fightersgeneration.com/np5/char/ssf2hd/bison-hdstance.gif",
        },
        
         
      ],
      amonster: { name: "", hp: 1, image: "", hp1: "" },
      monster: [
        
        {
          name: "Chun Li",
          hp: 500,
          image:
            "https://i.pinimg.com/originals/2f/f0/ca/2ff0ca6f9152fae4626610c9561b4e73.gif",
        },
        {
          name: "Ryu",
          hp: 480,
          image:
            "https://i.pinimg.com/originals/0c/d9/e0/0cd9e01d093e2297137017204e5ee5cb.gif",
        },
        {
          name: "Hugo",
          hp: 320,
          image: "https://64.media.tumblr.com/b2a8683c5d9ed44b902ffb3d34b85975/tumblr_inline_p7j08h6U3J1ri065t_250.gif",
        },
        {
          name: "Terry",
          hp: 365,
          image: "https://i.pinimg.com/originals/20/c4/79/20c479231b9ad48e02ceb6666bed9aa7.gif",
        },
        {
          name: "Wrestler",
          hp: 500,
          image: "https://thumbs.gfycat.com/BaggyGaseousKoi-size_restricted.gif",
        }
      
        
      ],
      pmax: "",
      mmax: "",
    };
  },
  methods: {
    randomno: function (min, max) {
      return Math.max(Math.floor(Math.random() * max) + 1, min);
    },
    start: function () {
      this.aplayer = this.player[this.randomno(1, 7) - 1];
      this.amonster = this.monster[this.randomno(1, 7) - 1];
    },
    attack: function () {
      this.pmax = Math.floor(Math.random() * 10 + 4);
      this.amonster.hp = this.amonster.hp - this.pmax;
      this.mmax = Math.floor(Math.random() * 10 + 4);
      this.aplayer.hp = this.aplayer.hp - this.mmax;
      if (this.aplayer.hp <= 0) {
        this.aplayer.hp = 0;
        this.end = true;
      } else if (this.amonster.hp <= 0) {
        this.amonster.hp = 0;
        this.end = true;
      }
    },
    special: function () {
      this.pmax = Math.floor(Math.random() * 15 + 6);
      this.amonster.hp = this.amonster.hp - this.pmax;
      this.mmax = Math.floor(Math.random() * 15 + 6);
      this.aplayer.hp = this.aplayer.hp - this.mmax;
      if (this.aplayer.hp <= 0) {
        this.aplayer.hp = 0;
        this.end = true;
      } else if (this.amonster.hp <= 0) {
        this.amonster.hp = 0;
        this.end = true;
      }
    },
    reset: function () {
      window.location.reload();
    },
  },
};
</script>
<style>
#score {
  font-size: 300%;
  color: aliceblue;
}
</style>