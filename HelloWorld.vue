<template>
  <div class="base-timer">
    <svg
      class="svg"
      viewBox="0 0 100 100"
      xmlns="http://www.w3.org/2000/svg"
    >
      <g class="circle">
        <circle
          class="path-elapsed"
          cx="50"
          cy="50"
          r="46.5"
        />
      </g>
    </svg>
    <span class="label">
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
