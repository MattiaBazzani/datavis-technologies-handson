<script>
    import { scaleLinear,scaleBand } from "d3-scale";
    import { extent } from "d3-array";
    import { axisBottom, axisLeft } from "d3-axis";
    import { select } from "d3-selection";
    // Dimensions
    const width = 600;
    const height = 300;
    const margin = { top: 10, right: 10, bottom: 30, left: 60 };
    const innerWidth = width - margin.left - margin.right;
    const innerHeight = height - margin.top - margin.bottom;
  
    // Array
    const data = [
      { service: "Netflix", viewers: 2.9 },
      { service: "Amazon Prime Video", viewers: 1.3 },
      { service: "Disney+", viewers: 2.1 },
      { service: "Hulu", viewers: 0.9 },
      { service: "Apple TV", viewers: 1.1 },
      { service: "Rakuten", viewers: 0.4 }
    ];

    const yScale = scaleLinear() .domain([0, 3]) .range([innerHeight, 0]);
    const xScale = scaleBand()
    .domain(data.map((d) => d.service))
    .range([0, innerWidth])
    .padding(0.2);
    const yAxis = (node) => axisLeft(yScale)(select(node));
    const xAxis = (node) => axisBottom(xScale)(select(node));
  </script>
  
  <!-- setting a viewBox and max-width allows the SVG to shrink but not grow! -->
  <svg viewbox="0 0 {width} {height}" style="max-width: {width}px">
    <g transform={`translate(${margin.left},${margin.top})`}>
      {#each data as d} 
        <rect x={xScale(d.service)} y={yScale(d.viewers)} width="40" height={innerHeight-yScale(d.viewers)}/>
      {/each}
      <g use:yAxis>
        <text class="ylabel" x={-innerHeight / 2} y={-margin.left / 2}>
          Viewers (Million)
        </text>
      </g>
      <g use:xAxis transform="translate(0,{innerHeight})" />
    </g>
  </svg>
  