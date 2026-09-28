# 🧠 Research Overview

<div class="research-overview-shell">
  <div class="research-overview-toolbar">
    <div class="research-overview-zoom" role="group" aria-label="Research map zoom controls">
      <button id="researchZoomOut" type="button" aria-label="Zoom out research map">−</button>
      <button id="researchZoomReset" type="button" aria-label="Reset research map zoom">100%</button>
      <button id="researchZoomIn" type="button" aria-label="Zoom in research map">+</button>
    </div>
  </div>
  <iframe id="researchFrame" src="research-overview.html" width="100%" height="800" frameborder="0" scrolling="no" title="Interactive research overview"></iframe>
  <a class="research-overview-full-link" href="research-overview.html" target="_blank" rel="noopener">View full map</a>
</div>

<style>
  .research-overview-toolbar,
  .research-overview-zoom,
  .research-overview-full-link {
    display: none;
  }

  @media (max-width: 767px) {
    .research-overview-shell {
      width: 100%;
    }

    .research-overview-toolbar {
      display: flex;
      align-items: center;
      justify-content: flex-end;
      margin-bottom: 0.45rem;
    }

    .research-overview-zoom {
      display: inline-flex;
      flex: 0 0 auto;
      overflow: hidden;
      border: 1px solid #d0d7de;
      border-radius: 6px;
      background: #fff;
    }

    .research-overview-zoom button {
      min-width: 2rem;
      height: 2rem;
      padding: 0 0.5rem;
      border: 0;
      border-right: 1px solid #d0d7de;
      background: #fff;
      color: #374151;
      font: inherit;
      font-size: 0.85rem;
      line-height: 1;
      cursor: pointer;
    }

    .research-overview-zoom button:last-child {
      border-right: 0;
    }

    .research-overview-zoom button:disabled {
      color: #9ca3af;
      cursor: default;
    }

    .research-overview-zoom button:focus-visible {
      position: relative;
      z-index: 1;
      outline: 2px solid #1e90ff;
      outline-offset: -2px;
    }

    #researchFrame {
      display: block;
      width: 100%;
      height: min(65vh, 560px);
      min-height: 360px;
      border: 1px solid #e1e4e8;
      border-radius: 6px;
      background: #fff;
      box-sizing: border-box;
      -webkit-overflow-scrolling: touch;
    }

    .research-overview-full-link {
      display: inline-block;
      margin-top: 0.45rem;
      font-size: 0.9rem;
    }
  }
</style>

<script>
  const researchFrame = document.getElementById("researchFrame");
  const researchMobileView = window.matchMedia("(max-width: 767px)");
  const researchZoomOut = document.getElementById("researchZoomOut");
  const researchZoomReset = document.getElementById("researchZoomReset");
  const researchZoomIn = document.getElementById("researchZoomIn");
  const researchZoomMin = 0.4;
  const researchZoomMax = 1.6;
  const researchZoomStep = 0.15;
  let researchZoom = 1;

  function applyResearchZoom(nextZoom) {
    researchZoom = Math.min(
      researchZoomMax,
      Math.max(researchZoomMin, Math.round(nextZoom * 100) / 100)
    );

    if (researchFrame.contentWindow?.setResearchZoom) {
      researchFrame.contentWindow.setResearchZoom(researchZoom);
    }

    researchZoomReset.textContent = `${Math.round(researchZoom * 100)}%`;
    researchZoomOut.disabled = researchZoom <= researchZoomMin;
    researchZoomIn.disabled = researchZoom >= researchZoomMax;
  }

  function updateResearchFrameMode() {
    researchFrame.setAttribute("scrolling", researchMobileView.matches ? "auto" : "no");
    resizeResearchFrame();
  }

  function resizeResearchFrame() {
    const frameDocument = researchFrame.contentDocument;
    if (!frameDocument || !frameDocument.body) return;

    if (researchMobileView.matches) {
      researchFrame.style.height = "";
      return;
    }

    researchFrame.style.height = `${Math.max(
      frameDocument.documentElement.scrollHeight,
      frameDocument.body.scrollHeight
    )}px`;
  }

  researchZoomOut.addEventListener("click", () => applyResearchZoom(researchZoom - researchZoomStep));
  researchZoomReset.addEventListener("click", () => applyResearchZoom(1));
  researchZoomIn.addEventListener("click", () => applyResearchZoom(researchZoom + researchZoomStep));
  researchFrame.addEventListener("load", () => {
    resizeResearchFrame();
    applyResearchZoom(1);
  });
  window.addEventListener("resize", resizeResearchFrame);
  researchMobileView.addEventListener("change", updateResearchFrameMode);
  updateResearchFrameMode();
</script>
