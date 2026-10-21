<script setup>
import { onBeforeUnmount, onMounted, ref, watch } from "vue";
import proxyBaseLogo from "../duckinglogo.png";

const mysteriumLogo = `${import.meta.env.BASE_URL}myst.png`;
const isMenuOpen = ref(false);
const isLightMode = ref(false);
const currentYear = new Date().getFullYear();
let revealObserver;

watch(isLightMode, (lightMode) => {
  document.documentElement.dataset.theme = lightMode ? "light" : "dark";
  document.querySelector('meta[name="theme-color"]').content = lightMode
    ? "#f5f4ef"
    : "#101311";
});

function closeMenu() {
  isMenuOpen.value = false;
}

onMounted(() => {
  if (
    !("IntersectionObserver" in window) ||
    window.matchMedia?.("(prefers-reduced-motion: reduce)")?.matches
  ) {
    return;
  }

  const elements = document.querySelectorAll("[data-reveal]");
  if (!elements.length) return;

  try {
    revealObserver = new IntersectionObserver(
      (entries, observer) => {
        entries.forEach((entry) => {
          if (!entry.isIntersecting) return;
          entry.target.classList.remove("reveal-pending");
          entry.target.classList.add("reveal-visible");
          observer.unobserve(entry.target);
        });
      },
      { threshold: 0.12, rootMargin: "0px 0px -6% 0px" },
    );

    elements.forEach((element) => {
      revealObserver.observe(element);
      element.classList.add("reveal-pending");
    });
  } catch {
    revealObserver?.disconnect();
    revealObserver = undefined;
    elements.forEach((element) => element.classList.remove("reveal-pending"));
  }
});

onBeforeUnmount(() => {
  revealObserver?.disconnect();
  revealObserver = undefined;
});
</script>

<template>
  <header class="site-header">
    <a class="wordmark" href="#top" aria-label="friendlyBrandon, home">
      friendlyBrandon<span>.</span>
    </a>
    <button
      class="menu-toggle"
      type="button"
      :aria-expanded="isMenuOpen"
      aria-controls="site-nav"
      @click="isMenuOpen = !isMenuOpen"
    >
      <span class="menu-toggle-label">Menu</span>
      <span class="menu-icon" aria-hidden="true"><i></i><i></i></span>
    </button>
    <nav
      id="site-nav"
      class="site-nav"
      :class="{ 'is-open': isMenuOpen }"
      aria-label="Main navigation"
    >
      <a href="#about" @click="closeMenu">About</a>
      <a href="#work" @click="closeMenu">Work</a>
      <a href="#community" @click="closeMenu">Community</a>
      <button
        class="theme-toggle"
        type="button"
        :aria-label="`Switch to ${isLightMode ? 'dark' : 'light'} mode`"
        :aria-pressed="isLightMode"
        @click="isLightMode = !isLightMode"
      >
        <span class="theme-icon" aria-hidden="true">{{ isLightMode ? "☾" : "☼" }}</span>
        <span class="theme-label">{{ isLightMode ? "Dark" : "Light" }} mode</span>
      </button>
      <a class="nav-contact" href="#contact" @click="closeMenu">
        Say hello <span aria-hidden="true">↗</span>
      </a>
    </nav>
  </header>

  <main id="top">
    <section class="hero section-wrap" aria-labelledby="hero-title">
      <div class="hero-copy">
        <p class="eyebrow"><span class="status-dot"></span> Graduate programming student</p>
        <h1 id="hero-title" data-reveal>Curious by nature.<br /><span>Developer</span> by practice.</h1>
        <p class="hero-intro" data-reveal>
          I’m friendlyBrandon — a graduate programming student learning by building useful
          software. My current toolkit includes C#, Java, and JavaScript.
        </p>
        <div class="hero-actions">
          <a class="button button-dark" href="#work">Explore my work <span aria-hidden="true">↓</span></a>
          <a class="text-link" href="#about">A little about me <span aria-hidden="true">↗</span></a>
        </div>
      </div>

      <div class="hero-art" aria-label="A visual illustration of a coding workspace">
        <div class="art-orbit orbit-one"></div>
        <div class="art-orbit orbit-two"></div>
        <div class="code-card">
          <div class="code-card-top"><span></span><span></span><span></span><small>hello.cs</small></div>
          <div class="code-lines" aria-hidden="true">
            <p><b>01</b><span class="code-purple">public class</span> <span class="code-green">Builder</span></p>
            <p><b>02</b>{</p>
            <p><b>03</b>&nbsp;&nbsp;<span class="code-purple">public string</span> Focus =&gt;</p>
            <p><b>04</b>&nbsp;&nbsp;&nbsp;&nbsp;<span class="code-yellow">"learn by making"</span>;</p>
            <p><b>05</b>}</p>
            <p class="cursor-line"><b>06</b><span class="cursor"></span></p>
          </div>
        </div>
        <div class="art-caption">Selected tools · C# / Java / JS</div>
      </div>
      <div class="hero-bottom">
        <span>SCROLL TO EXPLORE</span>
        <span class="scroll-line" aria-hidden="true"></span>
        <span>01 — 04</span>
      </div>
    </section>

    <section class="about section-wrap section-space" id="about" aria-labelledby="about-title">
      <div class="section-heading">
        <p class="eyebrow">01 / A bit about me</p>
        <h2 id="about-title" data-reveal>Building a foundation<br />for <span>what’s next.</span></h2>
      </div>
      <div class="about-content">
        <p class="large-copy" data-reveal>
          I’m a graduate programming student who enjoys turning ideas into real, working
          software. I’m building a broad foundation and getting hands-on with projects that
          connect code to everyday problems.
        </p>
        <p class="body-copy" data-reveal>
          I like learning how different parts of an application fit together — from a clear
          interface to the logic behind it. Outside of coursework, I also help out in the
          Mysterium Network community.
        </p>
        <div class="skills" aria-label="Programming languages">
          <span class="skill-label">LANGUAGES IN MY TOOLKIT</span>
          <div class="skill-list">
            <span><b class="skill-mark mark-csharp">C#</b> C sharp</span>
            <span><b class="skill-mark mark-java">☕</b> Java</span>
            <span><b class="skill-mark mark-js">JS</b> JavaScript</span>
          </div>
        </div>
      </div>
    </section>

    <section class="work section-wrap section-space" id="work" aria-labelledby="work-title">
      <div class="section-topline">
        <div class="section-heading">
          <p class="eyebrow">02 / Selected work</p>
          <h2 id="work-title" data-reveal>Projects with<br /><span>a purpose.</span></h2>
        </div>
        <a class="text-link all-projects" href="https://github.com/friendlyBrandon" target="_blank" rel="noreferrer">
          More on GitHub <span aria-hidden="true">↗</span>
        </a>
      </div>

      <article class="project-card aquafin">
        <div class="project-visual aqua-visual" aria-hidden="true">
          <div class="aqua-window">
            <div class="window-header"><span></span><span></span><span></span><b>aquafin / overview</b></div>
            <div class="aqua-dashboard">
              <div class="dashboard-title"><small>YOUR FLOOD PREPAREDNESS</small><strong>Rainfall outlook</strong></div>
              <div class="chart-labels"><span>JAN</span><span>MAR</span><span>MAY</span><span>JUL</span><span>SEP</span><span>NOV</span></div>
              <div class="chart">
                <span class="chart-grid grid-a"></span><span class="chart-grid grid-b"></span>
                <svg viewBox="0 0 400 120" role="presentation" preserveAspectRatio="none">
                  <path d="M0 87 C32 75 40 48 72 60 S118 100 145 72 S182 28 215 49 S260 92 288 57 S330 25 350 45 S380 69 400 21" />
                  <path class="chart-fill" d="M0 87 C32 75 40 48 72 60 S118 100 145 72 S182 28 215 49 S260 92 288 57 S330 25 350 45 S380 69 400 21 V120 H0 Z" />
                </svg>
              </div>
              <div class="forecast-row"><span><i></i> Forecast generated</span><strong>12 months</strong></div>
            </div>
          </div>
          <span class="visual-tag">Laravel + Python</span>
        </div>
        <div class="project-info">
          <div class="project-meta"><span>01</span><span>Full-stack · Forecasting</span></div>
          <h3>AquaFin</h3>
          <p data-reveal>
            A flood-preparedness platform that pairs a Laravel web app with a Python forecasting
            service. It turns rainfall predictions into helpful material recommendations, with
            dashboards, charts, and a materials cart.
          </p>
          <div class="project-tags"><span>Laravel</span><span>Python</span><span>Data visualization</span></div>
          <a class="project-link" href="https://github.com/friendlyBrandon/AquaFin_Project" target="_blank" rel="noreferrer">
            View project on GitHub <span aria-hidden="true">↗</span>
          </a>
        </div>
      </article>
    </section>

    <section class="community section-wrap section-space" id="community" aria-labelledby="community-title">
      <div class="section-heading">
        <p class="eyebrow">03 / Beyond the code</p>
        <h2 id="community-title" data-reveal>Good things happen<br /><span>in good communities.</span></h2>
      </div>
      <div class="community-grid">
        <article class="community-card mysterium-card">
          <div class="community-card-top"><span class="community-number">01</span><span class="community-arrow" aria-hidden="true">↗</span></div>
          <div class="mysterium-logo-wrap">
            <img
              :src="mysteriumLogo"
              alt="Mysterium Network logo"
              width="860"
              height="860"
              loading="eager"
              decoding="async"
            />
          </div>
          <p class="eyebrow">COMMUNITY HELPER</p>
          <h3>Mysterium Network</h3>
          <p class="body-copy" data-reveal>
            I help out in the Mysterium Network community — a decentralized VPN project —
            and enjoy being part of a community that cares about an open internet.
          </p>
          <a href="https://www.mysterium.network/" target="_blank" rel="noreferrer" class="community-link">
            Explore Mysterium Network <span aria-hidden="true">↗</span>
          </a>
        </article>
        <article class="community-card proxybase-card">
          <div class="community-card-top"><span class="community-number">02</span><span class="community-arrow" aria-hidden="true">↗</span></div>
          <div class="proxy-logo-wrap"><img :src="proxyBaseLogo" alt="ProxyBase logo" /></div>
          <p class="eyebrow">MY BUSINESS</p>
          <h3>ProxyBase</h3>
          <p class="body-copy" data-reveal>
            ProxyBase is my business, providing residential proxy access with usage-based pricing
            advertised from $0.75 per GB. Customers can add funds by card or cryptocurrency,
            starting at $1.
          </p>
          <div class="proxy-facts" aria-label="ProxyBase service details">
            <span><b>Residential</b> proxy network</span>
            <span><b>Flexible</b> pay-as-you-go top-ups</span>
          </div>
          <a href="https://proxybase.org/" target="_blank" rel="noreferrer" class="community-link">
            Explore ProxyBase <span aria-hidden="true">↗</span>
          </a>
        </article>
      </div>
    </section>

    <section class="contact section-wrap" id="contact" aria-labelledby="contact-title">
      <div class="contact-content">
        <p class="eyebrow">04 / Let’s connect</p>
        <h2 id="contact-title" data-reveal>Have a good one<br />in <span>mind?</span></h2>
        <p data-reveal>I’m always happy to connect, talk about projects, and learn something new.</p>
        <a class="button button-light" href="https://www.linkedin.com/in/birger-willemoons-83a1663b9" target="_blank" rel="noreferrer">
          Find me on LinkedIn <span aria-hidden="true">↗</span>
        </a>
      </div>
      <div class="contact-aside">
        <span class="contact-spark" aria-hidden="true">✳</span>
        <p>Curiosity is a<br />good place to start.</p>
        <a href="https://github.com/friendlyBrandon" target="_blank" rel="noreferrer">GitHub profile <span aria-hidden="true">↗</span></a>
      </div>
    </section>
  </main>

  <footer class="site-footer section-wrap">
    <a class="wordmark" href="#top" aria-label="Back to top">friendlyBrandon<span>.</span></a>
    <p>Designed &amp; built with curiosity.</p>
    <span>© {{ currentYear }} friendlyBrandon</span>
  </footer>
</template>
