# 🧠 Research Overview 

<!-- <meta charset="UTF-8" />
<link href="https://fonts.googleapis.com/css2?family=Lato:wght@200;300;400;600;700;900&display=swap"
    rel="stylesheet">  -->

<style>
    /* CSS for collapsible sections */
    .collapsible-header {
        cursor: pointer;
        padding: 10px;
        background-color: #f1f1f1;
        border: 1px solid #ddd;
        margin-bottom: 5px;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    .collapsible-content {
        display: none; /* Hidden by default */
        overflow: hidden;
        border: 1px solid #eee;
        border-top: none;
        padding: 10px;
    }
    .collapsible-header::after {
        content: '\02795'; /* Plus sign */
        font-size: 13px;
        color: #777;
        float: right;
        margin-left: 5px;
    }
    .collapsible-header.active::after {
        content: '\2796'; /* Minus sign */
    }
    /* D3.js Tree Styles */
    .link {
        fill: none;
        stroke: #555;
        stroke-opacity: 0.4;
        stroke-width: 1.5px;
    }

    .node circle {
        cursor: pointer;
    }

    .node text {
        cursor: pointer;
    }

    .node--internal circle {
        fill: #555;
    }

    .node--leaf circle {
        fill: #999;
    }

    .node text {
        font-family: 'Lato', sans-serif;
        font-size: 12px;
        fill: #000;
    }

    .node text[style*="1e90ff"] { /* Style for links */
        fill: #1e90ff;
    }
    #research-summary .collapsible-content {
        display: block; /* Show the collapsible content by default */
    }

    #research-summary .collapsible-header::after {
        content: '\2796'; /* Minus sign for the header */
    }

    #research-summary .collapsible-header {
        background-color: #e0e0e0; /* Optional: slight visual distinction for active state */
    }

    #clustrmaps {
        width: 200px !important; /* Adjust width as needed */
        height: 150px !important; /* Adjust height as needed */
        overflow: hidden;
    }

    #clustrmaps img, #clustrmaps iframe {
        width: 100% !important;
        height: 100% !important;
        object-fit: contain; /* Ensures the map scales properly */
    }
</style>

<div style="width:1000px;margin: 0px auto;">

    <div class="section" id="research-summary">
        <div class="collapsible-header">
            <h3>Research Directions</h3>
        </div>
        <div class="collapsible-content">
            <svg id="treeDiagram" width="1000" height="600" overflow="auto"></svg>
        </div>
        <div style="clear: both;"></div>
    </div>

<script>
    // JavaScript for collapsible sections
    var coll = document.getElementsByClassName("collapsible-header");
    let j;
    for (j = 0; j < coll.length; j++) {
        coll[j].addEventListener("click", function() {
            this.classList.toggle("active");
            const content = this.nextElementSibling;
            content.style.display = content.style.display === "block" ? "none" : "block";
        });
    }
</script>


<style>
    #toggle-collaborators {
        background: none;
        border: none;
        color: #007bff;
        cursor: pointer;
        padding: 0;
        font-size: 1em;
        text-decoration: underline;
    }
    #toggle-collaborators:hover {
        color: #0056b3;
    }
</style>

<script>
    function toggleCollaborators() {
        const shortList = document.getElementById('collaborators-short');
        const fullList = document.getElementById('collaborators-full');
        const button = document.getElementById('toggle-collaborators');
        
        if (fullList.style.display === 'none') {
            shortList.style.display = 'none';
            fullList.style.display = 'inline';
            button.textContent = 'Show less';
        } else {
            shortList.style.display = 'inline';
            fullList.style.display = 'none';
            button.textContent = 'Show more';
        }
    }
</script>
<script src="https://d3js.org/d3.v7.min.js"></script>

<script>
    // Data for the tree diagram
    const treeData = {
        "name": "Geometric Deep Learning",
        "children": [
            {
                "name": "Geometries",
                "children": [
                    { "name": "ALEM (TIP 24)", "url": "https://arxiv.org/abs/2303.15477" },
                    { "name": "PCM and BWCM", "url": "https://arxiv.org/abs/2407.02607" },
                ]
            },
            {
                "name": "Networks",
                "children": [
                    {
                        "name": "Normalization",
                        "children": [
                            { "name": "LieBN (ICLR24)", "url": "https://openreview.net/forum?id=okYdj8Ysru" },
                            { "name": "GyroBN (ICLR25)", "url": "https://openreview.net/forum?id=d1NWq4PjJW" },
                            { "name": "GBWBN (CVPR25)", "url": "https://arxiv.org/abs/2504.00660" },
                            { "name": "CBN (TNNLS25)", "url": "" }
                        ]
                    },
                    {
                        "name": "Classification",
                        "children": [
                            { "name": "SPD MLR (CVPR24)", "url": "https://arxiv.org/abs/2305.11288" },
                            { "name": "RMLR (NeurIPS24)", "url": "https://arxiv.org/abs/2409.19433" },
                        ]
                    },
                    {
                        "name": "Attention",
                        "children": [
                            { "name": "GDLNet (IJCAI24)", "url": "https://www.ijcai.org/proceedings/2024/0564.pdf" },
                            { "name": "CorAtt (IJCAI25)", "url": "" },
                        ]
                    },
                    {
                        "name": "Others",
                        "children": [
                            { "name": "Riemannian Local Mechanism (AAAI23)", "url": "https://arxiv.org/abs/2201.10145" },
                        ]
                    }
                ]
            },
            {
                "name": "Applications",
                "children": [
                    {
                        "name": "Covariance Pooling",
                        "children": [
                            { "name": "Understanding Covariance Pooling (ICLR25)", "url": "https://openreview.net/forum?id=q1t0Lmvhty" },
                        ]
                    },
                ]
            },
        ]
    };

    const svg = d3.select("#treeDiagram"),
        width = +svg.attr("width"),
        height = +svg.attr("height");

    const root = d3.hierarchy(treeData);

    // 先布置树布局（为了拿到 depth）
    const tree = d3.tree().size([height - 50, width - 100]);
    tree(root);

    // 计算总宽度：树深度 × 横向间距（120）
    const treeWidth = (root.height + 1) * 120;
    const offsetX = Math.max((width - treeWidth) / 2, 40);  // 保证最小留白为 40

    const g = svg.append("g").attr("transform", `translate(${offsetX},40)`);

    let i = 0; // Initialize a counter for node IDs

    // Assign unique IDs to initial nodes
    root.descendants().forEach(d => d.id = d.id || ++i);

    // Initial drawing
    update(root);

    // Update function for collapsing/expanding
    function update(source) {
        const duration = 750;

        // Compute the new tree layout.
        const nodes = root.descendants().reverse();
        const links = root.links();

        // Normalize for fixed-depth.
        nodes.forEach(d => { d.y = d.depth * 120; }); // Adjust this value to control node spacing horizontally

        // Update the nodes…
        const node = g.selectAll(".node")
            .data(nodes, d => d.id);

        // Enter any new nodes at the parent's previous position.
        const nodeEnter = node.enter().append("g")
            .attr("class", d => "node" + (d.children ? " node--internal" : " node--leaf"))
            .attr("transform", d => `translate(${source.y0},${source.x0})`)
            .on("click", click);

        nodeEnter.append("circle")
            .attr("r", 1e-6)
            .attr("fill", d => d._children ? "#555" : "#999")
            .attr("stroke", "#fff")
            .attr("stroke-width", 1);

        nodeEnter.append("text")
            .attr("dy", 3)
            .attr("x", d => d.children || d._children ? -8 : 8)
            .attr("text-anchor", d => d.children || d._children ? "end" : "start")
            .style("font-family", "'Lato', sans-serif")
            .style("font-size", "12px")
            .style("fill", d => d.data.url ? "#1e90ff" : "#000")
            .text(d => d.data.name)
            .style("fill-opacity", 1e-6)
            .on("click", (event, d) => {
                if (d.data.url) {
                    event.stopPropagation(); // Prevent node collapse/expand when clicking text link
                    window.open(d.data.url, "_blank");
                }
            });

        // Transition nodes to their new position.
        const nodeUpdate = nodeEnter.merge(node);

        nodeUpdate.transition()
            .duration(duration)
            .attr("transform", d => `translate(${d.y},${d.x})`);

        nodeUpdate.select("circle")
            .attr("r", 5)
            .attr("fill", d => d._children ? "#555" : "#999");

        nodeUpdate.select("text")
            .style("fill-opacity", 1);

        // Transition exiting nodes to the parent's new position.
        const nodeExit = node.exit().transition()
            .duration(duration)
            .attr("transform", d => `translate(${source.y},${source.x})`)
            .remove();

        nodeExit.select("circle")
            .attr("r", 1e-6);

        nodeExit.select("text")
            .style("fill-opacity", 1e-6);

        // Update the links…
        const link = g.selectAll(".link")
            .data(links, d => d.target.id);

        // Enter any new links at the parent's previous position.
        const linkEnter = link.enter().insert("path", "g")
            .attr("class", "link")
            .attr("d", d3.linkHorizontal()
                .x(d => source.y0)
                .y(d => source.x0));

        // Transition links to their new position.
        link.merge(linkEnter).transition()
            .duration(duration)
            .attr("d", d3.linkHorizontal()
                .x(d => d.y)
                .y(d => d.x));

        // Transition exiting links to the parent's new position.
        link.exit().transition()
            .duration(duration)
            .attr("d", d3.linkHorizontal()
                .x(d => source.y)
                .y(d => source.x))
            .remove();

        // Stash the old positions for transition.
        nodes.forEach(d => {
            d.x0 = d.x;
            d.y0 = d.y;
        });
    }

    // Toggle children on click.
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

    // Store initial positions for transition
    root.x0 = root.x;
    root.y0 = root.y;
</script>

