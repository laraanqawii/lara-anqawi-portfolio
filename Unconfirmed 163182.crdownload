(function () {
  'use strict';

  var root = document.documentElement;
  var menuToggle = document.querySelector('.menu-toggle');
  var nav = document.getElementById('primary-nav');
  var themeToggle = document.querySelector('.theme-toggle');
  var navLinks = Array.prototype.slice.call(document.querySelectorAll('.nav__link'));
  var reducedMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches;

  /* Mobile menu */
  function setMenu(open) {
    menuToggle.setAttribute('aria-expanded', String(open));
    nav.classList.toggle('nav--open', open);
  }

  menuToggle.addEventListener('click', function () {
    setMenu(menuToggle.getAttribute('aria-expanded') !== 'true');
  });

  nav.addEventListener('click', function (event) {
    if (event.target.closest('a')) setMenu(false);
  });

  document.addEventListener('keydown', function (event) {
    if (event.key === 'Escape' && nav.classList.contains('nav--open')) {
      setMenu(false);
      menuToggle.focus();
    }
  });

  /* Theme toggle. With no saved choice the page follows the OS setting. */
  function isDark() {
    var theme = root.dataset.theme;
    if (theme) return theme === 'dark';
    return window.matchMedia('(prefers-color-scheme: dark)').matches;
  }

  function syncThemeButton() {
    themeToggle.setAttribute('aria-pressed', String(isDark()));
  }

  themeToggle.addEventListener('click', function () {
    var next = isDark() ? 'light' : 'dark';
    root.dataset.theme = next;
    try { localStorage.setItem('theme', next); } catch (e) { /* storage unavailable */ }
    syncThemeButton();
  });

  syncThemeButton();

  /* Footer year */
  var year = document.querySelector('[data-year]');
  if (year) year.textContent = new Date().getFullYear();

  if (!('IntersectionObserver' in window)) return;

  /* Active section highlight: mark the link whose section crosses the upper third of the viewport. */
  var sections = navLinks
    .map(function (link) { return document.querySelector(link.getAttribute('href')); })
    .filter(Boolean);

  var sectionObserver = new IntersectionObserver(function (entries) {
    entries.forEach(function (entry) {
      if (!entry.isIntersecting) return;
      navLinks.forEach(function (link) {
        if (link.getAttribute('href') === '#' + entry.target.id) {
          link.setAttribute('aria-current', 'true');
        } else {
          link.removeAttribute('aria-current');
        }
      });
    });
  }, { rootMargin: '-30% 0px -65% 0px' });

  sections.forEach(function (section) { sectionObserver.observe(section); });

  /* Reveal on scroll. Only content that starts below the fold is hidden,
     so the first screen is always complete and nothing waits on JS. */
  if (reducedMotion) return;

  var revealObserver = new IntersectionObserver(function (entries, observer) {
    entries.forEach(function (entry) {
      if (!entry.isIntersecting) return;
      entry.target.classList.remove('reveal--pending');
      observer.unobserve(entry.target);
    });
  }, { rootMargin: '0px 0px -10% 0px' });

  document.querySelectorAll('.reveal').forEach(function (el) {
    if (el.getBoundingClientRect().top > window.innerHeight) {
      el.classList.add('reveal--pending');
      revealObserver.observe(el);
    }
  });
})();
