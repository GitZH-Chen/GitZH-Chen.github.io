# 🧠 Research Overview 


<svg id="treeDiagram" width="1000" height="600" overflow="auto"></svg>
<script src="https://d3js.org/d3.v7.min.js"></script>
<script>
    // Data for the tree diagram
    const treeData = {
        "name": "Research Work",
        "children": [
            {
                "name": "Diffusion Acceleration",
                "children": [
                    { "name": "Rectified Diffusion: Straightness Is Not Your Need (ICLR 2025)", "url": "https://arxiv.org/abs/2410.07303" },
                    { "name": "InstantPortrait: One-Step Portrait Editing (ICLR 2025)", "url": "https://openreview.net/forum?id=ZkFMe3OPfw" },
                    {},
                    {
                        "name": "Consistency Models",
                        "children": [
                            { "name": "Consistency Distillation" },
                            { "name": "Consistency Training" },
                            { "name": "Stable Consistency Tuning (ICLR 2025 Workshop)", "url": "https://arxiv.org/abs/2410.18958" }
                        ]
                    },

                    {
                        "name": "Phased Consistency Model (NeurIPS 2024)",
                        "children": [
                            { "name": "AnimateLCM (SIGGRAPH Asia 2024)", "url": "https://animatelcm.github.io" },
                            { "name": "OSV: One Step is Enough for High-Quality I2V (CVPR 2025)", "url": "https://arxiv.org/pdf/2409.11367" },
                            {
                                "name": "FastVideo",
                                "children": [
                                    { "name": "FastHunyuan" },
                                    { "name": "FastWAN" }
                                ]
                            },
                            {
                                "name": "Unleashing VDM for Fast Shape Generation (CVPR 2025)",
                                "children": [
                                    { "name": "Huanyuan-3D Turbo" }
                                ]
                            }
                        ]
                    },
                ]
            },
            {
                "name": "Reinforcement Learning",
                "children": [
                    {
                        "name": "Diffusion-NPO (ICLR 2025)",
                        "children": [
                            { "name": "Self-NPO: Data-Free NPO" }
                        ]
                    },
                    { "name": "Diffusion-Sharpening" }
                ]
            },
            {
                "name": "Generative Vision Applications",
                "children": [
                    { "name": "GS-DiT  (CVPR 2025)", "url": "https://arxiv.org/abs/2501.02690" },
                    { "name": "ZoLA: Zero-Shot Creative Long Animation Generation (ECCV 2024)", "url": "https://gen-l-2.github.io/" },
                    { "name": "Be-Your-Outpainter (ECCV 2024)", "url": "https://be-your-outpainter.github.io/" },
                    { "name": "Motion-I2V: Image-to-Video Generation with Explicit Motion Modeling (SIGGRAPH 2024)", "url": "https://xiaoyushi97.github.io/Motion-I2V/" },
                    { "name": "Rethinking the Spatial Inconsistency in CFG (CVPR 2024)", "url": "https://arxiv.org/abs/2404.05384" },
                ]
            },
            {
                "name": "Class-Incremental Learning",
                "children": [
                    {
                        "name": "PyCIL (SCIS)",
                        "children": [
                            { "name": "FOSTER  (ECCV 2022)", "url": "https://arxiv.org/abs/2204.04662" },
                            { "name": "BEEF (ICLR 2023)", "url": "https://openreview.net/forum?id=iP77_axu0h3" },
                            { "name": "FACT  (CVPR 2022)", "url": "https://arxiv.org/abs/2203.06953" }
                        ]
                    }
                ]
            }
        ]
    };

    // Set up SVG
    const svg = d3.select("#treeDiagram"),
        width = +svg.attr("width"),
        height = +svg.attr("height"),
        g = svg.append("g").attr("transform", "translate(40,40)");

    let i = 0; // Initialize a counter for node IDs

    // Tree layout
    const tree = d3.tree().size([height - 50, width - 100]);
    const root = d3.hierarchy(treeData);
    tree(root);
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
        nodes.forEach(d => { d.y = d.depth * 180; }); // Adjust this value to control node spacing horizontally

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