# 🧠 Research Overview

<iframe id="researchFrame" src="research-overview.html" width="100%" height="800" frameborder="0" scrolling="no"></iframe>

<script>
  const researchFrame = document.getElementById("researchFrame");

  function resizeResearchFrame() {
    const frameDocument = researchFrame.contentDocument;
    if (!frameDocument) return;

    researchFrame.style.height = `${Math.max(
      frameDocument.documentElement.scrollHeight,
      frameDocument.body.scrollHeight
    )}px`;
  }

  researchFrame.addEventListener("load", resizeResearchFrame);
  window.addEventListener("resize", resizeResearchFrame);
</script>
