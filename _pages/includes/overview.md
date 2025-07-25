# 🧠 Research Overview 
<!-- <p align="center">
  <img src="images/others/geometric_deep_learning.jpg" alt="Geometric Deep Learning Mindmap" width="100%">
</p> -->

<div id="tree-container" style="width: 100%; overflow-x: auto;">
  <svg id="treeDiagram" width="960" height="600"></svg>
</div>

<style>
  .link {
    fill: none;
    stroke: #ccc;
    stroke-width: 2px;
  }

  .node circle {
    fill: #999;
    stroke: steelblue;
    stroke-width: 1.5px;
  }

  .node text {
    font: 12px 'Lato', sans-serif;
    fill: black;
  }

  .node text:hover {
    fill: #1e90ff;
    cursor: pointer;
  }
</style>

<script src="https://d3js.org/d3.v7.min.js"></script>

<script>
const treeData = {
  name: "Research Work",
  children: [
    {
      name: "Diffusion Acceleration",
      children: [
        { name: "Rectified Diffusion", url: "https://arxiv.org/abs/2410.07303" },
        { name: "InstantPortrait", url: "https://openreview.net/forum?id=ZkFMe3OPfw" },
        {
          name: "Consistency Models",
          children: [
            { name: "Distillation" },
            { name: "Training" },
            { name: "Stable Tuning", url: "https://arxiv.org/abs/2410.18958" }
          ]
        }
      ]
    }
  ]
};

const width = 960;
const height = 600;
let i = 0;

const svg = d3.select("#treeDiagram")
  .append("g")
  .attr("transform", "translate(40,40)");

const treeLayout = d3.tree().size([height - 80, width - 160]);
const root = d3.hierarchy(treeData);
root.x0 = height / 2;
root.y0 = 0;

treeLayout(root);
update(root);

function update(source) {
  const nodes = root.descendants();
  const links = root.links();

  nodes.forEach(d => d.y = d.depth * 180);

  // Nodes
  const node = svg.selectAll("g.node")
    .data(nodes, d => d.id || (d.id = ++i));

  const nodeEnter = node.enter().append("g")
    .attr("class", "node")
    .attr("transform", d => `translate(${source.y0},${source.x0})`)
    .on("click", click);

  nodeEnter.append("circle")
    .attr("r", 5);

  nodeEnter.append("text")
    .attr("dy", 3)
    .attr("x", d => d.children || d._children ? -10 : 10)
    .style("text-anchor", d => d.children || d._children ? "end" : "start")
    .text(d => d.data.name)
    .on("click", (event, d) => {
      if (d.data.url) {
        event.stopPropagation();
        window.open(d.data.url, "_blank");
      }
    });

  // Links
  const link = svg.selectAll("path.link")
    .data(links, d => d.target.id);

  link.enter().insert("path", "g")
    .attr("class", "link")
    .attr("d", d3.linkHorizontal()
      .x(d => d.y)
      .y(d => d.x));
}

function click(event, d) {
  if (d.children) {
    d._children = d.children;
    d.children = null;
  } else {
    d.children = d._children;
    d._children = null;
  }
  update(d);
}
</script>

