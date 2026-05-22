(function () {
  const qs = new URLSearchParams(window.location.search);

  function toast(message) {
    let el = document.querySelector('.casa-toast');
    if (!el) {
      el = document.createElement('div');
      el.className = 'casa-toast';
      document.body.appendChild(el);
    }
    el.textContent = message;
    el.classList.add('show');
    clearTimeout(el._timer);
    el._timer = setTimeout(() => el.classList.remove('show'), 2200);
  }

  function pageName() {
    return location.pathname.split('/').pop() || 'index.html';
  }

  function collectSearch() {
    const search = document.querySelector('.search');
    const nav = document.querySelector('.nav-search');
    const whereInput = search?.querySelector('input[type="text"]');
    const whereText = nav?.querySelector('.seg .v')?.textContent;
    return {
      where: (whereInput?.value || qs.get('where') || whereText || 'Lake District').trim(),
      dates: qs.get('dates') || '12-19 Jul',
      guests: qs.get('guests') || '2 adults'
    };
  }

  function goToBrowse(overrides = {}) {
    const state = { ...collectSearch(), ...overrides };
    const next = new URL('browse.html', window.location.href);
    Object.entries(state).forEach(([key, value]) => {
      if (value) next.searchParams.set(key, value);
    });
    window.location.href = next.pathname + next.search;
  }

  window.goSearch = function (ev) {
    if (ev?.currentTarget?.classList?.contains('seg')) {
      document.querySelectorAll('.search .seg').forEach((seg) => seg.classList.remove('active'));
      ev.currentTarget.classList.add('active');
      return;
    }
    goToBrowse();
  };

  function hydrateSearchText() {
    const where = qs.get('where');
    const dates = qs.get('dates');
    const guests = qs.get('guests');
    const navSearch = document.querySelector('.nav-search');
    if (navSearch) {
      const values = navSearch.querySelectorAll('.seg .v');
      if (where && values[0]) values[0].textContent = where;
      if (dates && values[1]) values[1].textContent = dates.replace('-', ' - ');
      if (guests && values[2]) values[2].textContent = guests;
      navSearch.addEventListener('click', () => goToBrowse());
    }
    const heroInput = document.querySelector('.search input[type="text"]');
    if (heroInput && where) heroInput.value = where;
  }

  function setupSearch() {
    hydrateSearchText();
    document.querySelectorAll('.search .seg').forEach((seg) => {
      seg.addEventListener('click', (ev) => window.goSearch(ev));
    });
    document.querySelectorAll('.search-go, .nav-search .go').forEach((button) => {
      button.addEventListener('click', (ev) => {
        ev.preventDefault();
        ev.stopPropagation();
        goToBrowse();
      });
    });
    document.querySelectorAll('.search input[type="text"]').forEach((input) => {
      input.addEventListener('keydown', (ev) => {
        if (ev.key === 'Enter') goToBrowse({ where: input.value.trim() });
      });
    });
  }

  function saveKey(button) {
    const card = button.closest('.pc, .title-row, .post-prop, .gallery, .ps-card') || button.parentElement;
    const label = card?.querySelector('.pc-title, h1, .pname, .ps-title')?.textContent?.trim()
      || card?.querySelector('.ph')?.dataset?.label
      || pageName();
    return 'casa:saved:' + label.toLowerCase().replace(/\s+/g, '-');
  }

  function setupSaves() {
    document.querySelectorAll('.save-heart, .save-btn').forEach((button) => {
      const key = saveKey(button);
      if (localStorage.getItem(key) === '1') button.classList.add('saved');
      button.addEventListener('click', (ev) => {
        ev.preventDefault();
        ev.stopPropagation();
        button.classList.toggle('saved');
        localStorage.setItem(key, button.classList.contains('saved') ? '1' : '0');
        const label = button.querySelector('span');
        if (label) label.textContent = button.classList.contains('saved') ? 'Saved' : 'Save';
        toast(button.classList.contains('saved') ? 'Saved to your list' : 'Removed from saved');
      });
    });
  }

  function setupFilterLinks() {
    document.querySelectorAll('.qf .chip, .tag-wall .ch, .county-pill, .cat-tile, .fb-pill').forEach((el) => {
      el.addEventListener('click', (ev) => {
        const href = el.getAttribute('href');
        if (href && href !== '#') return;
        ev.preventDefault();
        const text = el.textContent.trim().replace(/\s+/g, ' ');
        if (pageName() === 'feed.html') {
          toast('Showing ' + text);
          document.querySelectorAll('.county-pill, .side-link, .feed-tab').forEach((x) => x.classList.remove('active'));
          el.classList.add('active');
        } else {
          goToBrowse({ where: text.replace(/^#/, '') });
        }
      });
    });
  }

  function setupBrowseControls() {
    if (pageName() !== 'browse.html') return;
    const activeWhere = qs.get('where');
    if (activeWhere) {
      const h = document.querySelector('.head-strip h1');
      const meta = document.querySelector('.head-strip .h-meta');
      if (h) h.innerHTML = `Stays around <i>${activeWhere}</i>`;
      if (meta) meta.innerHTML = `<span class="n">214</span> matching stays<br>fee-free direct booking`;
    }
    document.querySelectorAll('.mini-map .pin').forEach((pin) => {
      pin.addEventListener('click', () => {
        document.querySelectorAll('.mini-map .pin').forEach((p) => p.classList.remove('active'));
        pin.classList.add('active');
        toast('Highlighted stay at ' + pin.textContent.trim() + ' per night');
      });
    });
  }

  function setupFeed() {
    if (pageName() !== 'feed.html') return;
    document.querySelectorAll('.post-type-pill, .feed-tab, .side-link').forEach((button) => {
      button.addEventListener('click', () => {
        const group = button.classList.contains('feed-tab') ? '.feed-tab'
          : button.classList.contains('side-link') ? '.side-link'
          : '.post-type-pill';
        document.querySelectorAll(group).forEach((x) => x.classList.remove(group === '.post-type-pill' ? 'on' : 'active'));
        button.classList.add(group === '.post-type-pill' ? 'on' : 'active');
      });
    });
    const postButton = document.querySelector('.post-btn');
    const textarea = document.querySelector('.compose textarea');
    postButton?.addEventListener('click', () => {
      const text = textarea?.value.trim();
      if (!text) {
        toast('Write a quick post first');
        return;
      }
      const card = document.createElement('article');
      card.className = 'post';
      card.innerHTML = `<div class="ph-head"><div class="av guest">J</div><div class="who"><div class="nm"><span class="name">James</span><span class="badge">New post</span></div><div class="meta-line"><span class="when">Just now</span><span class="dot"></span><span>Casa member</span></div></div></div><div class="body">${text.replace(/[<>&]/g, (c) => ({'<':'&lt;','>':'&gt;','&':'&amp;'}[c]))}</div>`;
      document.querySelector('.feed-col .feed-tabs')?.after(card);
      textarea.value = '';
      toast('Posted to the community feed');
    });
  }

  function setupAuth() {
    document.querySelectorAll('.submit-btn').forEach((button) => {
      button.addEventListener('click', (ev) => {
        ev.preventDefault();
        localStorage.setItem('casa:joined', '1');
        toast(button.textContent.toLowerCase().includes('sign') ? 'Welcome back' : 'Account created for the prototype');
        setTimeout(() => {
          window.location.href = document.querySelector('.role-card.sel')?.textContent.includes('host') ? 'list.html' : 'profile.html';
        }, 550);
      });
    });
  }

  function setupPrototypeLinks() {
    document.querySelectorAll('a[href="#"]').forEach((link) => {
      link.addEventListener('click', (ev) => {
        ev.preventDefault();
        toast('Prototype placeholder - this page comes next');
      });
    });
  }

  document.addEventListener('DOMContentLoaded', () => {
    setupSearch();
    setupSaves();
    setupFilterLinks();
    setupBrowseControls();
    setupFeed();
    setupAuth();
    setupPrototypeLinks();
  });
})();
