# 🔔 News

<style>
.news-panel { --news-pubs: #245b96; --news-talks: #7045a0; --news-awards: #805b13; --news-service: #176b59; }
.news-panel .news-filters { display: flex; flex-wrap: wrap; gap: 6px; margin: 0 0 14px; }
.news-panel .news-filters[hidden] { display: none; }
.news-panel .news-filter { --filter-color: #535b65; --filter-bg: #f3f5f7; --filter-active: #e0e5eb; font: inherit; font-size: .85em; font-weight: 600; line-height: 1.4; padding: 5px 11px; border: 1px solid transparent; border-radius: 4px; background: var(--filter-bg); color: var(--filter-color); cursor: pointer; margin: 0; }
.news-panel .news-filter:hover { background: var(--filter-active); }
.news-panel .news-filter[aria-pressed="true"] { background: var(--filter-active); border-color: var(--filter-color); box-shadow: inset 0 0 0 1px var(--filter-color); }
.news-panel .news-filter:focus-visible { outline: 2px solid var(--filter-color); outline-offset: 3px; }
.news-panel .news-list { max-height: 400px; overflow-y: auto; padding: 0 8px 0 0; margin: 0; list-style: none; }
.news-panel .news-list li { position: relative; margin: 0; padding: 7px 0 7px 5em; line-height: 1.65; }
.news-panel .news-list li[hidden] { display: none; }
.news-panel .news-tag { position: absolute; left: 0; top: calc(7px + .3em); box-sizing: border-box; width: 6em; text-align: center; font-size: .75em; font-weight: 600; line-height: 1.5; padding: 1px 6px; border-radius: 4px; white-space: nowrap; }
.news-panel .news-pubs { color: var(--news-pubs); background: #eaf2fc; }
.news-panel .news-talks { color: var(--news-talks); background: #f2ecfa; }
.news-panel .news-awards { color: var(--news-awards); background: #faf1db; }
.news-panel .news-service { color: var(--news-service); background: #e6f4ef; }
</style>
<div class="news-panel" id="news-panel">
  <div class="news-filters" role="group" aria-label="Filter news" hidden>
    <button class="news-filter" type="button" data-filter="all" aria-pressed="true" aria-controls="news-list">All <span class="news-count"></span></button>
    <button class="news-filter" type="button" data-filter="pubs" aria-pressed="false" aria-controls="news-list">Pubs</button>
    <button class="news-filter" type="button" data-filter="talks" aria-pressed="false" aria-controls="news-list">Talks</button>
    <button class="news-filter" type="button" data-filter="awards" aria-pressed="false" aria-controls="news-list">Awards</button>
    <button class="news-filter" type="button" data-filter="service" aria-pressed="false" aria-controls="news-list">Service</button>
  </div>
  <ul class="news-list" id="news-list">
  <li data-category="talks"><span class="news-tag news-talks">Talks</span> <strong>2026.09</strong>: Invited talk on deep learning over Riemannian spaces at <a href="https://www.ntu.edu.sg/spms/news-events/events/detail/2026/09/28/default-calendar/ias-frontiers-conference-on-geometry--dynamics--and-learning">GDL2026</a>.</li>
  <li data-category="talks"><span class="news-tag news-talks">Talks</span> <strong>2026.08</strong>: Invited tutorial on deep learning over Riemannian spaces at <a href="https://mlss2026.is.tuebingen.mpg.de/">MLSS 2026</a>.</li>
  <li data-category="pubs"><span class="news-tag news-pubs">Pubs</span> <strong>2026.08</strong>: Manifold embedding accepted to EMNLP 2026 (review score: <a href="https://stats.aclrollingreview.org/iterations/2026/may/">top 0.5%</a>). Congrats to Xianglong!</li>
  <li data-category="pubs"><span class="news-tag news-pubs">Pubs</span> <strong>2026.07</strong>: Riemannian t-SNE accepted to TMLR. Congrats to Rui and Bin!</li>
  <li data-category="talks"><span class="news-tag news-talks">Talks</span> <strong>2026.07</strong>: Invited talk on hyperbolic deep learning at <a href="https://workshopagrt.github.io/conference/2026/">IWAG 2026</a>.</li>
  <li data-category="awards"><span class="news-tag news-awards">Awards</span> <strong>2026.07</strong>: Awarded an <a href="https://www.eliza.school/">ELIZA PhD Mobility Scholarship</a> (3,000 EUR).</li>
  <li data-category="awards"><span class="news-tag news-awards">Awards</span> <strong>2026.06</strong>: Awarded 190,000 GPU hours through <a href="https://www.hpc.cineca.it/hpc-access/access-cineca-resources/iscra-projects/">CINECA ISCRA</a>.</li>
  <li data-category="pubs"><span class="news-tag news-pubs">Pubs</span> <strong>2026.05</strong>: Bures–Wasserstein attention accepted to KDD 2026. Congrats to Shaocheng!</li>
  <li data-category="service"><span class="news-tag news-service">Service</span> <strong>2026.05</strong>: We are organizing <a href="https://mlss2026.is.tuebingen.mpg.de/">MLSS 2026</a> in T&uuml;bingen (Aug. 31-Sept. 11, 2026). Welcome to <a href="https://mlss2026.is.tuebingen.mpg.de/apply/">apply</a>!</li>
  <li data-category="pubs"><span class="news-tag news-pubs">Pubs</span> <strong>2026.05</strong>: Riemannian GCN for skeleton-based two-person interaction recognition accepted to IJCAI 2026. Congrats to Rui and Zihao!</li>
  <li data-category="service"><span class="news-tag news-service">Service</span> <strong>2026.05</strong>: Awarded the <a href="https://icml.cc/Conferences/2026/ProgramCommittee">ICML 2026 Gold Reviewer Award</a>.</li>
  <li data-category="pubs"><span class="news-tag news-pubs">Pubs</span> <strong>2026.04</strong>: Riemannian networks over correlation matrices accepted to ICML 2026.</li>
  <li data-category="awards"><span class="news-tag news-awards">Awards</span> <strong>2026.04</strong>: Awarded 360,000 GPU hours through <a href="https://www.eurohpc-ju.europa.eu/">EuroHPC</a>.</li>
  <li data-category="pubs"><span class="news-tag news-pubs">Pubs</span> <strong>2026.02</strong>: Hyperbolic Busemann neural networks accepted to CVPR 2026.</li>
  <li data-category="pubs"><span class="news-tag news-pubs">Pubs</span> <strong>2026.01</strong>: Five papers accepted to ICLR 2026. Congrats to Zihan, Xianglong, Shanglin, and Chen!</li>
  <li data-category="awards"><span class="news-tag news-awards">Awards</span> <strong>2026.01</strong>: Awarded the DAAD "Research Grants in Germany" scholarship, supporting a research stay at <a href="https://is.mpg.de/ei">MPI-IS Tübingen</a>.</li>
  <li data-category="pubs"><span class="news-tag news-pubs">Pubs</span> <strong>2025.11</strong>: Hyperbolic Wasserstein clustering accepted to AAAI 2026 for oral presentation. Congrats to Rui and Yuting!</li>
  <li data-category="talks"><span class="news-tag news-talks">Talks</span> <strong>2025.10</strong>: Invited tutorial on algebraic approaches to Riemannian deep learning at <a href="http://2025.prcv.cn/CN/Tutorial3/index.asp">PRCV 2025</a>.</li>
  <li data-category="pubs"><span class="news-tag news-pubs">Pubs</span> <strong>2025.09</strong>: Riemannian attention by gyrovector spaces (GyroAtt) accepted to NeurIPS 2025. Congrats to Rui and Chen!</li>
  <li data-category="pubs"><span class="news-tag news-pubs">Pubs</span> <strong>2025.07</strong>: Riemannian BatchNorm via the Cholesky geometry accepted in IEEE TNNLS. Congrats to Rui!</li>
  <li data-category="awards"><span class="news-tag news-awards">Awards</span> <strong>2025.07</strong>: Awarded an <a href="https://elsa-ai.eu/phd-postdoc/">ELSA Mobility Grant</a> (3,000 EUR).</li>
  <li data-category="awards"><span class="news-tag news-awards">Awards</span> <strong>2025.07</strong>: Awarded an <a href="https://elias-ai.eu/mobility-program/">ELIAS Mobility Grant</a> (2,400 EUR).</li>
  <li data-category="talks"><span class="news-tag news-talks">Talks</span> <strong>2025.06</strong>: Invited talk on Riemannian normalization at Jiangnan University.</li>
  <li data-category="pubs"><span class="news-tag news-pubs">Pubs</span> <strong>2025.04</strong>: Riemannian self-attention accepted to IJCAI 2025. Congrats to Chen!</li>
  <li data-category="pubs"><span class="news-tag news-pubs">Pubs</span> <strong>2025.04</strong>: CVPR25 & ICLR25 (high-order pooling) selected for <a href="https://valser.org/2025/#/poster">VALSE 2025</a>.</li>
  <li data-category="pubs"><span class="news-tag news-pubs">Pubs</span> <strong>2025.03</strong>: Riemannian approach for skeleton-based action recognition accepted in IEEE TIM. Congrats to Rui and Jiayao!</li>
  <li data-category="talks"><span class="news-tag news-talks">Talks</span> <strong>2025.03</strong>: Invited talk on Riemannian normalization and classification at the University of Alberta.</li>
  <li data-category="pubs"><span class="news-tag news-pubs">Pubs</span> <strong>2025.02</strong>: Riemannian BatchNorm for ill-conditioned SPD matrices accepted to CVPR 2025. Congrats to Rui and Shaocheng!</li>
  <li data-category="pubs"><span class="news-tag news-pubs">Pubs</span> <strong>2025.01</strong>: Two papers accepted to ICLR 2025: gyrogroup batchnorm (GyroBN) and Analyzing high-order pooling.</li>
  <li data-category="pubs"><span class="news-tag news-pubs">Pubs</span> <strong>2024.09</strong>: Riemannian classifier over general geometries (RMLR) accepted to NeurIPS 2024.</li>
  <li data-category="pubs"><span class="news-tag news-pubs">Pubs</span> <strong>2024.08</strong>: Adaptive Riemannian metrics accepted in IEEE TIP.</li>
  <li data-category="pubs"><span class="news-tag news-pubs">Pubs</span> <strong>2024.04</strong>: Grassmannian self-attention accepted to IJCAI 2024. Congrats to Rui and Chen!</li>
  <li data-category="pubs"><span class="news-tag news-pubs">Pubs</span> <strong>2024.03</strong>: CVPR24 paper selected for <a href="http://valser.org/2024/#/poster">VALSE 2024</a>.</li>
  <li data-category="talks"><span class="news-tag news-talks">Talks</span> <strong>2024.03</strong>: Internal talk on Riemannian geometry at Jiangnan University.</li>
  <li data-category="pubs"><span class="news-tag news-pubs">Pubs</span> <strong>2024.02</strong>: Riemannian classifier on SPD manifolds (SPDMLR) accepted to CVPR 2024.</li>
  <li data-category="pubs"><span class="news-tag news-pubs">Pubs</span> <strong>2024.01</strong>: Lie group BatchNorm (LieBN) accepted to ICLR 2024.</li>
  <li data-category="awards"><span class="news-tag news-awards">Awards</span> <strong>2023.12</strong>: Awarded the Excellent Master’s Thesis of Jiangsu Association of Artificial Intelligence (one of only 7 awards across Jiangsu Province).</li>
  </ul>
  <span class="news-status" role="status" aria-live="polite" style="position:absolute;width:1px;height:1px;padding:0;overflow:hidden;clip-path:inset(50%);white-space:nowrap;"></span>
</div>
<script>
(function () {
  const panel = document.getElementById('news-panel');
  const list = panel.querySelector('.news-list');
  const items = Array.from(list.querySelectorAll('li[data-category]'));
  const buttons = Array.from(panel.querySelectorAll('.news-filter'));
  buttons.forEach(function (button) {
    const category = button.dataset.filter;
    const count = category === 'all' ? items.length : items.filter(function (item) {
      return item.dataset.category === category;
    }).length;
    let counter = button.querySelector('.news-count');
    if (!counter) {
      counter = document.createElement('span');
      counter.className = 'news-count';
      button.append(' ', counter);
    }
    counter.textContent = '(' + count + ')';
  });
  panel.querySelector('.news-filters').hidden = false;
  buttons.forEach(function (button) {
    button.addEventListener('click', function () {
      const category = button.dataset.filter;
      let count = 0;
      items.forEach(function (item) {
        item.hidden = category !== 'all' && item.dataset.category !== category;
        if (!item.hidden) count++;
      });
      buttons.forEach(function (other) {
        other.setAttribute('aria-pressed', String(other === button));
      });
      list.scrollTop = 0;
      panel.querySelector('.news-status').textContent = count + ' news items shown';
    });
  });
})();
</script>
