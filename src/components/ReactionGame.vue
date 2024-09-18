<template>
  <div v-if="showBlock" class="block" @click="stopTimer">
    Click me
  </div>
</template>

<script>
export default {
  name: 'ReactionBlock', // Component name
  props: {
    delay: {
      type: Number,
      default: 1000,
    },
  },
  data(){
    return{
      showBlock:false,
      Timer:null,
      result:0
    }
  },
  mounted() {
    console.log(`Reaction delay set to: ${this.delay} ms`);
    setTimeout(() =>{
      this.showBlock=true
      this.startTimer()
    },this.delay)
  },
  methods: {
    handleClick() {
      console.log('Block clicked!'); // Optional: add a click handler
      // You can add more logic here if needed
    },
    startTimer(){
      this.Timer = setInterval(()=>{
        this.result += 10
      },10)
      console.log(this.result)
    },
    stopTimer(){
      clearInterval(this.Timer)
      this.$emit('end',this.result)
      this.showBlock=false
    }

  },
  
    
};
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: #ea2d3d;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
  cursor: pointer; /* Add pointer cursor for better UX */
}
</style>
