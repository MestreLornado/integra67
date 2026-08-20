/* ═══════════════════════════════════════════════════════════
   AquaSol CEP — script.js
   Menu mobile · smooth scroll · scrollspy · reveals · contadores
   · Disco de Newton · difração em CD · telemetria · simulador
   ═══════════════════════════════════════════════════════════ */
(function () {
  'use strict';

  const $  = (s, c) => (c || document).querySelector(s);
  const $$ = (s, c) => Array.from((c || document).querySelectorAll(s));
  const reduced = () => window.matchMedia('(prefers-reduced-motion: reduce)').matches;
  const fmt = (n, dec = 0) =>
    n.toLocaleString('pt-BR', { minimumFractionDigits: dec, maximumFractionDigits: dec });

  /* ── Ano corrente + carregamento ─────────────────────────── */
  $('#year').textContent = new Date().getFullYear();
  window.addEventListener('load', () => document.body.classList.add('loaded'));

  /* ── Cabeçalho: sombra + barra de progresso ──────────────── */
  const topbar = $('#topbar');
  const progress = $('#progressBar');
  function onScroll() {
    topbar.classList.toggle('is-scrolled', window.scrollY > 10);
    const h = document.documentElement;
    const max = h.scrollHeight - h.clientHeight;
    progress.style.width = (max > 0 ? (h.scrollTop / max) * 100 : 0) + '%';
  }
  window.addEventListener('scroll', onScroll, { passive: true });
  onScroll();

  /* ── Menu mobile ─────────────────────────────────────────── */
  const navToggle = $('#navToggle');
  const setMenu = (open) => {
    topbar.classList.toggle('menu-open', open);
    navToggle.setAttribute('aria-expanded', String(open));
  };
  navToggle.addEventListener('click', () =>
    setMenu(!topbar.classList.contains('menu-open'))
  );
  document.addEventListener('keydown', (e) => {
    if (e.key === 'Escape' && topbar.classList.contains('menu-open')) {
      setMenu(false); navToggle.focus();
    }
  });
  document.addEventListener('click', (e) => {
    if (topbar.classList.contains('menu-open') && !topbar.contains(e.target)) setMenu(false);
  });
  window.addEventListener('resize', () => {
    if (window.innerWidth > 920) setMenu(false);
  });

  /* ── Rolagem suave (respeita prefers-reduced-motion) ─────── */
  $$('a[href^="#"]').forEach((link) => {
    link.addEventListener('click', (e) => {
      const target = document.getElementById(link.getAttribute('href').slice(1));
      if (!target) return;
      e.preventDefault();
      target.scrollIntoView({ behavior: reduced() ? 'auto' : 'smooth', block: 'start' });
      setMenu(false);
      history.pushState(null, '', link.getAttribute('href'));
      // Move o foco para o destino (acessibilidade de teclado)
      target.setAttribute('tabindex', '-1');
      target.focus({ preventScroll: true });
    });
  });

  /* ── Scrollspy: destaque do link ativo ───────────────────── */
  const spyMap = {
    inicio: 'inicio',
    tecnociencia: 'tecnociencia',
    robotica: 'robotica',
    simulador: 'simulador',
    acessibilidade: 'acessibilidade',
    equipe: 'equipe'
  };
  const spyLinks = new Map($$('.menu a').map((a) => [a.getAttribute('href').slice(1), a]));
  const spy = new IntersectionObserver((entries) => {
    entries.forEach((en) => {
      if (!en.isIntersecting) return;
      const id = spyMap[en.target.id];
      spyLinks.forEach((a, key) => a.classList.toggle('is-active', key === id));
    });
  }, { rootMargin: '-40% 0px -55% 0px' });
  Object.keys(spyMap).forEach((id) => {
    const el = document.getElementById(id);
    if (el) spy.observe(el);
  });

  /* ── Revelação por scroll ─────────────────────────────────── */
  const io = new IntersectionObserver((entries) => {
    entries.forEach((en) => {
      if (en.isIntersecting) { en.target.classList.add('in'); io.unobserve(en.target); }
    });
  }, { threshold: 0.12 });
  $$('.reveal').forEach((el) => io.observe(el));

  /* ── Efeito decodificar no kicker do hero ─────────────────── */
  const kicker = $('#kicker');
  if (kicker && !reduced()) {
    const finalText = kicker.dataset.text;
    const glyphs = '▚▞▟#%&@01*+<>ABCDELUZ';
    let frame = 0;
    const timer = setInterval(() => {
      frame++;
      const solved = Math.floor(frame * finalText.length / 36);
      kicker.textContent = finalText.split('').map((ch, i) =>
        i < solved || ch === ' ' ? ch : glyphs[(Math.random() * glyphs.length) | 0]
      ).join('');
      if (solved >= finalText.length) { kicker.textContent = finalText; clearInterval(timer); }
    }, 38);
  }

  /* ── Contadores animados dos indicadores ──────────────────── */
  const animateCount = (el) => {
    const target = parseFloat(el.dataset.count);
    const dec = parseInt(el.dataset.dec || '0', 10);
    if (reduced()) { el.textContent = fmt(target, dec); return; }
    const dur = 1400, t0 = performance.now();
    const step = (t) => {
      const p = Math.min((t - t0) / dur, 1);
      el.textContent = fmt(target * (1 - Math.pow(1 - p, 3)), dec);
      if (p < 1) requestAnimationFrame(step);
    };
    requestAnimationFrame(step);
  };
  const ioCount = new IntersectionObserver((entries) => {
    entries.forEach((en) => {
      if (en.isIntersecting) { animateCount(en.target); ioCount.unobserve(en.target); }
    });
  }, { threshold: 0.6 });
  $$('.count').forEach((el) => ioCount.observe(el));

  /* ── Disco de Newton interativo ───────────────────────────── */
  const disc = $('#newtonDisc');
  const discBtn = $('#discBtn');
  const discCap = $('#discCaption');
  if (disc && discBtn) {
    discBtn.addEventListener('click', () => {
      if (reduced()) { // sem animação: mostra o resultado conceitual
        const merged = disc.classList.toggle('spinning');
        disc.style.filter = merged ? 'blur(1.5px) saturate(.6) brightness(1.25)' : '';
        discBtn.textContent = merged ? '■ Parar o disco' : '▶ Girar o disco';
        discBtn.setAttribute('aria-pressed', String(merged));
        discCap.textContent = merged
          ? 'Girando: as cores se somam e percebemos o branco (animação reduzida nas suas configurações).'
          : 'Em repouso, vemos 7 cores distintas.';
        return;
      }
      const spinning = disc.classList.toggle('spinning');
      discBtn.textContent = spinning ? '■ Parar o disco' : '▶ Girar o disco';
      discBtn.setAttribute('aria-pressed', String(spinning));
      discCap.textContent = spinning
        ? 'Girando rápido: as cores se somam e percebemos o branco — a prova de Newton!'
        : 'Em repouso, vemos 7 cores distintas.';
    });
  }

  /* ── Demonstração: difração em rede de CD ─────────────────── */
  const cdLab = $('#cdLab');
  const cdBtn = $('#cdBtn');
  const cdCap = $('#cdCaption');
  if (cdLab && cdBtn) {
    cdBtn.addEventListener('click', () => {
      const on = cdLab.classList.toggle('diffracting');
      cdBtn.textContent = on ? '◑ Desativar difração' : '◐ Ativar difração';
      cdBtn.setAttribute('aria-pressed', String(on));
      cdCap.textContent = on
        ? 'Cores separadas por difração: o vermelho (maior λ) desvia mais que o violeta — o oposto do prisma.'
        : 'Luz branca incide sobre as trilhas do CD.';
    });
  }

  /* ── Telemetria ilustrativa (Robótica) ────────────────────── */
  const telTemp = $('#telTemp'), telLux = $('#telLux'), telPanel = $('#telPanel');
  if (telTemp) {
    let w = 29.4, p = 41.8;
    setInterval(() => {
      w = Math.min(31.5, Math.max(28.2, w + (Math.random() - 0.5) * 0.4));
      p = Math.min(44,   Math.max(39,   p + (Math.random() - 0.5) * 0.8));
      telTemp.textContent  = fmt(w, 1);
      telPanel.textContent = fmt(p, 1);
      telLux.textContent   = fmt(620 + Math.round(Math.random() * 360));
    }, 1800);
  }

  /* ═══════════════════════════════════════════════════════════
     SIMULADOR DE AQUECIMENTO SOLAR
     Física simplificada: aquecimento proporcional à captação,
     resfriamento natural em direção à temperatura ambiente.
     ═══════════════════════════════════════════════════════════ */
  const sim = {
    on: false, cloudy: false, temp: 22,
    AMBIENT: 22, TARGET: 34,
    timer: null,
    flags: { warm: false, done: false }
  };

  const el = {
    power:  $('#simPower'),  cloud: $('#simCloud'), reset: $('#simReset'),
    stage:  $('#simStage'),  temp:  $('#simTemp'),  state: $('#simState'),
    pump:   $('#stPump'),    watts: $('#stPower'),  lux:   $('#stLux'),
    delta:  $('#stDelta'),   fill:  $('#thermoFill'), announce: $('#simAnnounce')
  };

  const say = (msg) => { if (el.announce) el.announce.textContent = msg; };

  function render() {
    // Temperatura (pt-BR usa vírgula)
    el.temp.textContent = fmt(sim.temp, 1);

    // Termômetro: escala didática 20–40 °C
    const pct = Math.max(0, Math.min(1, (sim.temp - 20) / 20)) * 100;
    el.fill.style.height = pct + '%';

    // Aquecimento visual da água (0 → 1)
    const warmth = Math.max(0, Math.min(1, (sim.temp - 24) / (sim.TARGET - 24)));
    el.stage.style.setProperty('--warmth', warmth.toFixed(2));

    // Estados visuais
    el.stage.dataset.state   = sim.on ? 'on' : 'off';
    el.stage.dataset.cloudy  = String(sim.cloudy);

    // Painel de dados
    if (sim.on) {
      const base = sim.cloudy ? 340 : 860;
      const luxBase = sim.cloudy ? 320 : 980;
      el.watts.textContent = fmt(base + Math.round(Math.random() * 24 - 12)) + ' W';
      el.lux.textContent   = fmt(luxBase + Math.round(Math.random() * 40 - 20)) + ' lx';
      el.pump.textContent  = 'em circulação ✔';
      el.pump.style.color  = 'var(--aqua-dp)';
    } else {
      el.watts.textContent = '0 W';
      el.lux.textContent = '—';
      el.pump.textContent = 'desligada';
      el.pump.style.color = '';
    }

    const delta = sim.TARGET - sim.temp;
    el.delta.textContent = delta <= 0 ? 'meta atingida ✔' : fmt(delta, 1) + ' °C';

    // Estado textual
    if (!sim.on) {
      el.state.dataset.state = 'off';
      el.state.textContent = sim.temp > sim.AMBIENT + 0.5
        ? '● Sistema em espera — água esfriando lentamente'
        : '● Sistema em espera';
    } else if (sim.temp >= sim.TARGET) {
      el.state.dataset.state = 'done';
      el.state.textContent = '● Meta atingida! Temperatura estável em ' + fmt(sim.TARGET, 0) + ' °C';
    } else {
      el.state.dataset.state = 'on';
      el.state.textContent = sim.cloudy ? '● Aquecendo (captação reduzida — céu nublado)' : '● Aquecendo — bomba em circulação';
    }
  }

  function tick() {
    if (sim.on) {
      // Taxa menor quando nublado e quando se aproxima da meta
      const proximity = 1 - Math.max(0, (sim.temp - (sim.TARGET - 3)) / 3) * 0.6;
      sim.temp += (sim.cloudy ? 0.018 : 0.052) * proximity;
      if (sim.temp >= sim.TARGET) { sim.temp = sim.TARGET; }
    } else {
      // Resfriamento natural em direção à temperatura ambiente
      sim.temp += (sim.AMBIENT - sim.temp) * 0.004;
    }

    // Anúncios para leitores de tela (somente marcos importantes)
    if (sim.on && !sim.flags.warm && sim.temp >= 28) {
      sim.flags.warm = true;
      say('A água atingiu 28 graus Celsius: início da faixa de conforto.');
    }
    if (sim.on && !sim.flags.done && sim.temp >= sim.TARGET) {
      sim.flags.done = true;
      say('Meta de 34 graus atingida. O sistema manterá a temperatura estável.');
    }

    render();
  }

  function startTimer() {
    stopTimer();
    sim.timer = setInterval(tick, 110);
  }
  function stopTimer() {
    if (sim.timer) { clearInterval(sim.timer); sim.timer = null; }
  }

  if (el.power) {
    el.power.addEventListener('click', () => {
      sim.on = !sim.on;
      el.power.setAttribute('aria-pressed', String(sim.on));
      el.power.innerHTML = sim.on ? '■ Desligar Sistema Solar' : '⚡ Ligar Sistema Solar';

      if (sim.on) {
        sim.flags.done = false;
        say('Sistema solar ligado. Bomba em circulação, iniciando aquecimento da água.');
        startTimer();
      } else {
        say('Sistema desligado. A água esfriará lentamente até a temperatura ambiente.');
        // mantém o timer ativo para o resfriamento ser visível
      }
      render();
    });

    el.cloud.addEventListener('change', () => {
      sim.cloudy = el.cloud.checked;
      if (sim.on) {
        say(sim.cloudy
          ? 'Dia nublado ativado: captação solar reduzida.'
          : 'Céu limpo novamente: captação solar total.');
      }
      render();
    });

    el.reset.addEventListener('click', () => {
      sim.on = false; sim.cloudy = false; sim.temp = sim.AMBIENT;
      sim.flags = { warm: false, done: false };
      el.cloud.checked = false;
      el.power.setAttribute('aria-pressed', 'false');
      el.power.innerHTML = '⚡ Ligar Sistema Solar';
      stopTimer();
      render();
      say('Simulação reiniciada: água a 22 graus e sistema desligado.');
    });

    render(); // estado inicial
  }
})();
