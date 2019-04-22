<template>
  <div id="output-container">
    <div v-if="loading">Loading...</div>
    <div v-else id="console">
      <div id="room-desc" >
        <p id="txt">
           {{roomDesc}}
        </p>
      
      </div>
      <div id="photo">
        <img :src="image" alt="img">
      </div>
      <div id="err-msg">{{errorMsg}}</div>
      <div id="input">
        <input v-model="input" @keydown.enter="command" ref="input" placeholder="Enter here...">
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Output",
  data() {
    return {
      empty: true,
      key: false,
      teddy: false,
      loading: true,
      room: null,
      roomDesc: "",
      input: "",
      rooms: null,
      initialRoom: "Entrance",
      image: "",
      errorMsg: ""
    };
  },
  mounted() {
    fetch("./data/rooms.json")
      .then(results => results.json())
      .then(results => {
      
        this.rooms = results;
        this.room = this.rooms[this.initialRoom];
        this.roomDesc = this.room.description;
        this.image = this.room.img;
     
        this.loading = false;
     
        this.$nextTick(() => {
          this.$refs.input.focus();
        });
      });
  },
  methods: {
    command() {
      

      if (!this.validateInput(this.input)) {
        this.errorMsg = "Invalid Command! : " +this.input;
        this.input = "";
        return;
      } else {
        let action = "";
        let arg = this.input;
        this.errorMsg = "";
        const dir = ["north", "south", "east", "west"];
        for (let i = 0; dir.length > i; i++){
          if (dir[i] == arg){
             action = "movement";
            break;
          }
        }
     switch (action) {
        case "movement": {
          this.initiateMove(arg);
        }
      }
     this.input = "";
      }
     
    },
    initiateMove(d) {
      let chosenDir = d;
      //for now, only takes whole terms, (north not n)

     // console.log("Chosen direction:" + chosenDir);
      for (let i = 0; i < this.room.moves.length; i++) {
        if (this.room.moves[i].direction === chosenDir) {
          this.room = this.rooms[this.room.moves[i].room];
          this.roomDesc = this.room.description;
          this.image = this.room.img;
          return;
        } 
      }
      this.errorMsg = "Invalid Command! : " +this.input;
      // alert ()
    },
    validateInput(i) {
      let valid = ["north", "south", "east", "west"];
      //checks if input is included in "valid" array
      // add check if included in moves for this.room
      return valid.includes(i.toLowerCase());
    },
    
  }
};
</script>
<style lang="scss" scoped>
@import "../scss/main.scss";
#output-container {
  width: 40%;
  margin: auto;
  border: black solid 1px;
  text-align: left;
  position: relative;
  padding: 1em;
  background: #000;
  #console {
    @extend %reset;
    @include flex(flex, row wrap, center, center);
      flex:2 1 auto;
    #room-desc {
      padding-right:1em;
      width: 50%;
     
    }
      img {
        padding:1.5em 0 1.5em 0;
        width: 15em;
        overflow:none;
      }
      #err-msg {  
      height:3em;
      width:100%;
      text-align:center;
      padding:.5em;
      font-size: 1.25em;
      
    }
    input {
      background-color: rgba(34, 34, 34, 0.836);
      color: rgba(255, 255, 255, 0.678);
      border: none;
      width: 100%;
      position: absolute;
      bottom: 0;
      left: 0;
      overflow: hidden;
    }
    input:focus,
    textarea:focus {
      outline: none;
    }
  }
}
</style>



