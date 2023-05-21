<script>
  // Dimensions
  import { scaleLog } from "d3-scale";
  import { axisBottom } from "d3-axis";
  import { select } from "d3-selection";
  const width = 800;
  const height = 100;
  const margin = { top: 5, right: 5, bottom: 25, left: 5 };
  const innerWidth = width - margin.left - margin.right;
  const innerHeight = height - margin.top - margin.bottom;
  const scale = scaleLog() .domain([1, 10]) .range([0, innerWidth]);
  const xAxis = (node) => axisBottom(scale)(select(node));
  const y=innerHeight/2
  const values = [2, 4, 6, 7, 9];
</script>




<svg viewBox="0 0 {width} {height}">
  <g transform="translate({margin.left},{margin.top})">
    {#each values as v}
      <circle cx={scale(v)} cy={y} r="10" />
    {/each}
    <g use:xAxis transform="translate(0,{innerHeight})">
      <text x={innerWidth/2} y = '25' text-anchor='middle' fill='currentcolor'>
      x label
      </text>
    </g>
  </g>
</svg>
