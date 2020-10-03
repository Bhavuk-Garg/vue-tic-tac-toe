<template>
  <div>
      <Board :squares="squares" :winner="winner" @click="moveRegister"/>
      <GameMessage v-if="!!winner" :color="playerColor">
          <p>Game won by {{player}}</p>
          <v-btn @click="restart">Restart</v-btn>    
      </GameMessage>
      <GameMessage v-else-if="moves>8">
          <p>It's a draw</p>
          <v-btn @click="restart">Restart</v-btn>
      </GameMessage>
      <GameMessage v-else :color="playerColor">
          Player {{player}} Move
      </GameMessage>
  </div>
</template>

<script>
export default {
    components:{
        Board: ()=> import('./Board'),
        GameMessage: ()=> import('./GameMessage')
    },
    data(){
        return {
            squares: Array(9).fill(null),
            player: 'X',
            winner: null,
            moves: 0
        }
    },
    methods:{
        restart(){
            this.squares=Array(9).fill(null);
            this.winner=null;
            this.moves=0;
        },
        hasWon(){
            console.log(this.squares)
         const matches = [
                [0, 1, 2], [3, 4, 5], [6, 7, 8], [0, 3, 6], [1, 4, 7],
                [2, 5, 8], [0, 4, 8], [2, 4, 6]
            ]
            for(let i=0;i<matches.length;i++){
                let [a,b,c]=matches[i];
                let squares=this.squares;
                if(squares[a] && squares[a]===squares[b] && squares[a]===squares[c])
                {
                    this.winner=[a,b,c]
                    return true;
                }
            }
            return false;
        },
        moveRegister(index){
            if(this.squares[index]!=null || this.winner==true)   return 
            this.$set(this.squares,index,this.player)
            if(this.hasWon())
                return;
            this.moves++;
            this.player= this.player=='X'?'O':'X';
        }
    },
    computed:{
        playerColor(){
            return this.player=='X'?'purple':'orange';
        }
    }
}
</script>

<style>

</style>