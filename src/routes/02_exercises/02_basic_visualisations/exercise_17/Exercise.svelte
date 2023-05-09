<script>
    // Dimensions
    import { scaleLog } from "d3-scale";
    const width = 800;
    const height = 100;
    const margin = { top: 5, right: 5, bottom: 5, left: 5 };
    const innerWidth = width - margin.left - margin.right;
    const innerHeight = height - margin.top - margin.bottom;
    const scale = scaleLog() .domain([1, 10]) .range([0, innerWidth]);
    const y=innerHeight/2
    const values = [2, 4, 6, 7, 9];
  </script>
  

  

  <svg viewBox="0 0 {width} {height}">
    <g transform="translate({margin.left},{margin.top})">
      {#each values as v}
        <circle cx={scale(v)} cy={y} r="10" />
      {/each}
    </g>
  </svg>
  