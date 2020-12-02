<template>
  <div class="">
    <span class="">
      {{ formattedTimeLeft }}
    </span>
  </div>
</template>

<script>
export default {
  props: {
    timeLeft: {
      type: Number,
      required: true
    }
  }
}
</script>


<style scope lang="css">
.base-timer {
  position: relative;
  width: 300px;
  height: 300px;}

  .circle {
    fill: none;
    stroke: none;
  }
  .label {
  position: relative;   
    
    /* Size should match the parent container */    
    width: 300px;
    height: 300px;
    /* Keep the label aligned to the top */    
    top: 0;
    /* Create a flexible box that centers content vertically and horizontally */    
    display: flex;
    align-items: center;
    justify-content: center;
    /* Sort of an arbitrary number; adjust to your liking */
    font-size: 48px;
  }
  .path-elapsed {
    stroke-width: 7px;
    stroke:grey;
  }

</style>
