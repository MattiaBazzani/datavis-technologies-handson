<script>
    
    import { extent } from "d3-array";
    import { scaleLinear } from "d3-scale";
    import { scaleOrdinal } from "d3-scale";
    import { schemeDark2 } from "d3-scale-chromatic";
    // Dimensions
    const width = 800;
    const height = 100;
    const margin = { top: 20, right: 5, bottom: 5, left: 5 };
    const innerWidth = width - margin.left - margin.right;
    const innerHeight = height - margin.top - margin.bottom;
 
    // Array
    const values = [
      { x: 2, y: 1, category: "cat1" },
      { x: 4, y: 2, category: "cat3" },
      { x: 6, y: 1, category: "cat2" },
      { x: 7, y: 3, category: "cat3" },
      { x: 9, y: 1, category: "cat2" }
    ];

    const xScale = scaleLinear() .domain([1, 10]) .range([0, innerWidth]);
    const yScale = scaleLinear() .domain([0, 4]) .range([innerHeight, 0]);
    const cScale = scaleOrdinal(schemeDark2).domain(extent(values, (d) => d.category));
  </script>
  
  <svg viewBox="0 0 {width} {height}">
    <g transform="translate({margin.left},{margin.top})">
      {#each values as v}
      <line
        x1={xScale(v.x)}
        x2={xScale(v.x)}
        y1={yScale(v.y)}
        y2={innerHeight}
        stroke="black"
      />

      <circle cx={xScale(v.x)} cy={yScale(v.y)} r="10" fill={cScale(v.category)}/>
        
      <text x={xScale(v.x)} y={yScale(v.y)-10}>
        {v.y}
      </text> 
      {/each}
    <line
      x1="0"
      x2={innerWidth}
      y1={innerHeight}
      y2={innerHeight}
      stroke="black"
    />
    </g>
  </svg>
  
  <style>
    text {
      text-anchor: middle;
      font-size: small;
    }
  </style>
  