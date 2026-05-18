# portofolioVA
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>VYTA ANDRI — AI-Powered Executive Operations Specialist</title>
<meta name="description" content="Executive Virtual Assistant & AI-Powered Operations Specialist with 6+ years experience across e-commerce, F&B, and business operations.">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=DM+Mono:ital,wght@0,300;0,400;0,500;1,300&family=Outfit:wght@200;300;400;500;600;700;800;900&display=swap" rel="stylesheet">
<style>
:root {
  --bg-primary: #080a0f;
  --bg-secondary: #0d1117;
  --bg-card: rgba(10, 15, 25, 0.7);
  --cyan: #00d4ff;
  --cyan-dim: rgba(0, 212, 255, 0.15);
  --cyan-glow: rgba(0, 212, 255, 0.4);
  --blue: #0066ff;
  --silver: #a8b5c8;
  --silver-dim: rgba(168, 181, 200, 0.4);
  --glass: rgba(255,255,255,0.03);
  --glass-border: rgba(0, 212, 255, 0.12);
  --glass-border-hover: rgba(0, 212, 255, 0.35);
  --text-primary: #e8edf5;
  --text-secondary: #7a8fa8;
  --text-muted: #3d4f63;
  --font-display: 'Outfit', sans-serif;
  --font-body: 'Space Grotesk', sans-serif;
  --font-mono: 'DM Mono', monospace;
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

html { scroll-behavior: smooth; font-size: 16px; }

body {
  background: var(--bg-primary);
  color: var(--text-primary);
  font-family: var(--font-body);
  overflow-x: hidden;
  cursor: none;
}

/* CUSTOM CURSOR */
.cursor {
  position: fixed;
  width: 10px; height: 10px;
  background: var(--cyan);
  border-radius: 50%;
  pointer-events: none;
  z-index: 9999;
  transform: translate(-50%,-50%);
  transition: transform 0.1s, width 0.2s, height 0.2s, opacity 0.2s;
  mix-blend-mode: screen;
}
.cursor-ring {
  position: fixed;
  width: 36px; height: 36px;
  border: 1px solid rgba(0,212,255,0.5);
  border-radius: 50%;
  pointer-events: none;
  z-index: 9998;
  transform: translate(-50%,-50%);
  transition: transform 0.12s ease, width 0.3s, height 0.3s, border-color 0.3s;
}
body:hover .cursor { opacity: 1; }

/* LOADING SCREEN */
#loader {
  position: fixed; inset: 0;
  background: var(--bg-primary);
  z-index: 9000;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 24px;
  transition: opacity 0.8s ease, visibility 0.8s;
}
#loader.hidden { opacity: 0; visibility: hidden; pointer-events: none; }

.loader-text {
  font-family: var(--font-mono);
  font-size: 11px;
  letter-spacing: 0.3em;
  color: var(--cyan);
  text-transform: uppercase;
  animation: blink 1.2s infinite;
}
@keyframes blink { 0%,100%{opacity:1} 50%{opacity:0.3} }

.loader-bar-wrap {
  width: 280px; height: 1px;
  background: rgba(0,212,255,0.1);
  position: relative; overflow: hidden;
}
.loader-bar {
  height: 100%;
  background: linear-gradient(90deg, transparent, var(--cyan), transparent);
  width: 60%;
  animation: scanBar 1.4s ease-in-out infinite;
}
@keyframes scanBar {
  0% { transform: translateX(-100%); }
  100% { transform: translateX(280px); }
}
.loader-logo {
  font-family: var(--font-display);
  font-size: 13px;
  font-weight: 800;
  letter-spacing: 0.4em;
  color: var(--text-muted);
  text-transform: uppercase;
}

/* PARTICLES CANVAS */
#particles-canvas {
  position: fixed; inset: 0;
  pointer-events: none;
  z-index: 0;
  opacity: 0.4;
}

/* GRID OVERLAY */
.grid-overlay {
  position: fixed; inset: 0;
  background-image:
    linear-gradient(rgba(0,212,255,0.025) 1px, transparent 1px),
    linear-gradient(90deg, rgba(0,212,255,0.025) 1px, transparent 1px);
  background-size: 80px 80px;
  pointer-events: none;
  z-index: 0;
}

/* NAV */
nav {
  position: fixed; top: 0; left: 0; right: 0;
  z-index: 100;
  padding: 20px 40px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  background: rgba(8,10,15,0.6);
  backdrop-filter: blur(24px);
  -webkit-backdrop-filter: blur(24px);
  border-bottom: 1px solid rgba(0,212,255,0.06);
  transition: padding 0.3s;
}
.nav-logo {
  font-family: var(--font-mono);
  font-size: 12px;
  letter-spacing: 0.25em;
  color: var(--cyan);
  text-transform: uppercase;
  display: flex; align-items: center; gap: 10px;
}
.nav-logo::before {
  content: '';
  width: 6px; height: 6px;
  background: var(--cyan);
  border-radius: 50%;
  box-shadow: 0 0 8px var(--cyan);
  animation: pulse 2s infinite;
}
@keyframes pulse { 0%,100%{opacity:1;transform:scale(1)} 50%{opacity:0.5;transform:scale(0.8)} }

.nav-links {
  display: flex; gap: 32px;
  list-style: none;
}
.nav-links a {
  font-family: var(--font-mono);
  font-size: 11px;
  letter-spacing: 0.15em;
  color: var(--text-secondary);
  text-decoration: none;
  text-transform: uppercase;
  transition: color 0.2s;
  position: relative;
}
.nav-links a::after {
  content: '';
  position: absolute; bottom: -4px; left: 0; right: 0;
  height: 1px; background: var(--cyan);
  transform: scaleX(0); transition: transform 0.2s;
}
.nav-links a:hover { color: var(--cyan); }
.nav-links a:hover::after { transform: scaleX(1); }
.nav-cta {
  font-family: var(--font-mono);
  font-size: 11px;
  letter-spacing: 0.15em;
  color: var(--cyan);
  text-transform: uppercase;
  border: 1px solid rgba(0,212,255,0.3);
  padding: 8px 20px;
  text-decoration: none;
  transition: all 0.2s;
  background: rgba(0,212,255,0.04);
}
.nav-cta:hover {
  background: rgba(0,212,255,0.12);
  border-color: var(--cyan);
  box-shadow: 0 0 20px rgba(0,212,255,0.2);
}

/* SECTIONS */
section { position: relative; z-index: 1; }

/* HERO */
#hero {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 120px 40px 80px;
  overflow: hidden;
  text-align: center;
}
.hero-eyebrow {
  font-family: var(--font-mono);
  font-size: 11px;
  letter-spacing: 0.4em;
  color: var(--cyan);
  text-transform: uppercase;
  margin-bottom: 28px;
  opacity: 0;
  animation: fadeUp 0.8s 1.5s forwards;
  display: flex; align-items: center; gap: 16px;
}
.hero-eyebrow::before, .hero-eyebrow::after {
  content: '';
  width: 40px; height: 1px;
  background: linear-gradient(90deg, transparent, var(--cyan));
}
.hero-eyebrow::after { background: linear-gradient(90deg, var(--cyan), transparent); }

.hero-name {
  font-family: var(--font-display);
  font-size: clamp(36px, 6vw, 80px);
  font-weight: 800;
  letter-spacing: -0.01em;
  line-height: 1.05;
  color: var(--text-primary);
  opacity: 0;
  animation: fadeUp 0.8s 1.7s forwards;
  position: relative;
}
.hero-name span {
  background: linear-gradient(135deg, #fff 30%, var(--cyan) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
.hero-sub {
  font-family: var(--font-body);
  font-size: clamp(14px, 1.8vw, 18px);
  font-weight: 300;
  color: var(--text-secondary);
  margin-top: 20px;
  letter-spacing: 0.04em;
  opacity: 0;
  animation: fadeUp 0.8s 1.9s forwards;
  max-width: 520px;
}
.hero-btns {
  display: flex; gap: 16px;
  margin-top: 44px;
  opacity: 0;
  animation: fadeUp 0.8s 2.1s forwards;
  flex-wrap: wrap;
  justify-content: center;
}
.btn-primary {
  font-family: var(--font-mono);
  font-size: 12px;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  padding: 14px 36px;
  background: linear-gradient(135deg, rgba(0,212,255,0.15), rgba(0,102,255,0.1));
  border: 1px solid rgba(0,212,255,0.4);
  color: var(--cyan);
  text-decoration: none;
  transition: all 0.25s;
  position: relative; overflow: hidden;
}
.btn-primary::before {
  content: '';
  position: absolute; inset: 0;
  background: linear-gradient(135deg, rgba(0,212,255,0.25), rgba(0,102,255,0.15));
  opacity: 0; transition: opacity 0.25s;
}
.btn-primary:hover::before { opacity: 1; }
.btn-primary:hover {
  box-shadow: 0 0 30px rgba(0,212,255,0.3), inset 0 0 20px rgba(0,212,255,0.05);
  border-color: var(--cyan);
}
.btn-secondary {
  font-family: var(--font-mono);
  font-size: 12px;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  padding: 14px 36px;
  border: 1px solid rgba(168,181,200,0.15);
  color: var(--silver);
  text-decoration: none;
  transition: all 0.25s;
  background: transparent;
}
.btn-secondary:hover {
  border-color: rgba(168,181,200,0.4);
  color: var(--text-primary);
}

/* HERO STATS */
.hero-stats {
  display: flex; gap: 40px;
  margin-top: 60px;
  opacity: 0;
  animation: fadeUp 0.8s 2.3s forwards;
  flex-wrap: wrap;
  justify-content: center;
}
.hero-stat {
  text-align: center;
  padding: 20px 28px;
  background: var(--glass);
  border: 1px solid var(--glass-border);
  backdrop-filter: blur(12px);
  position: relative;
}
.hero-stat::before {
  content: '';
  position: absolute; top: 0; left: 0; right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, var(--cyan), transparent);
}
.stat-num {
  font-family: var(--font-display);
  font-size: 28px;
  font-weight: 700;
  color: var(--cyan);
  letter-spacing: -0.02em;
}
.stat-label {
  font-family: var(--font-mono);
  font-size: 9px;
  letter-spacing: 0.2em;
  color: var(--text-secondary);
  text-transform: uppercase;
  margin-top: 4px;
}

/* FLOATING HOLOGRAM PANELS */
.holo-orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(80px);
  pointer-events: none;
}
.orb-1 {
  width: 500px; height: 500px;
  background: radial-gradient(circle, rgba(0,212,255,0.08), transparent 70%);
  top: -100px; right: -100px;
}
.orb-2 {
  width: 400px; height: 400px;
  background: radial-gradient(circle, rgba(0,102,255,0.07), transparent 70%);
  bottom: -50px; left: -80px;
}
.orb-3 {
  width: 300px; height: 300px;
  background: radial-gradient(circle, rgba(0,212,255,0.05), transparent 70%);
  top: 50%; left: 50%;
  transform: translate(-50%,-50%);
}

/* SCAN LINE */
.scan-line {
  position: absolute; left: 0; right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(0,212,255,0.3), transparent);
  animation: scanDown 4s linear infinite;
  pointer-events: none;
}
@keyframes scanDown { 0%{top:0%} 100%{top:100%} }

@keyframes fadeUp {
  from { opacity: 0; transform: translateY(24px); }
  to { opacity: 1; transform: translateY(0); }
}
@keyframes fadeIn {
  from { opacity: 0; } to { opacity: 1; }
}
@keyframes float {
  0%,100% { transform: translateY(0); }
  50% { transform: translateY(-12px); }
}

/* SECTION LAYOUT */
.section-wrap { max-width: 1160px; margin: 0 auto; padding: 100px 40px; }
.section-header {
  margin-bottom: 64px;
  display: flex;
  align-items: center;
  gap: 24px;
}
.section-label {
  font-family: var(--font-mono);
  font-size: 10px;
  letter-spacing: 0.35em;
  color: var(--cyan);
  text-transform: uppercase;
  writing-mode: vertical-lr;
  transform: rotate(180deg);
}
.section-title {
  font-family: var(--font-display);
  font-size: clamp(28px, 4vw, 48px);
  font-weight: 700;
  line-height: 1.1;
  letter-spacing: -0.02em;
  color: var(--text-primary);
}
.section-title em {
  font-style: normal;
  background: linear-gradient(135deg, var(--cyan), #0066ff);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
.section-divider {
  height: 1px;
  background: linear-gradient(90deg, var(--cyan), transparent);
  margin-top: 12px;
  max-width: 180px;
}

/* ABOUT */
#about { background: linear-gradient(180deg, transparent, rgba(0,212,255,0.02), transparent); }
.about-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 48px;
  align-items: start;
}
.about-text p {
  color: var(--text-secondary);
  line-height: 1.8;
  margin-bottom: 20px;
  font-size: 15px;
  font-weight: 300;
}
.about-text p strong {
  color: var(--text-primary);
  font-weight: 500;
}
.about-highlight {
  border-left: 2px solid var(--cyan);
  padding-left: 20px;
  margin: 28px 0;
  font-family: var(--font-display);
  font-size: 16px;
  font-weight: 500;
  color: var(--text-primary);
  line-height: 1.6;
}
.metrics-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}
.metric-card {
  background: var(--glass);
  border: 1px solid var(--glass-border);
  padding: 24px;
  position: relative;
  overflow: hidden;
  transition: all 0.3s;
  animation: float 5s ease-in-out infinite;
  backdrop-filter: blur(12px);
}
.metric-card:nth-child(2) { animation-delay: -1.5s; }
.metric-card:nth-child(3) { animation-delay: -3s; }
.metric-card:nth-child(4) { animation-delay: -4.5s; }
.metric-card:hover {
  border-color: var(--glass-border-hover);
  box-shadow: 0 0 30px rgba(0,212,255,0.1), inset 0 0 20px rgba(0,212,255,0.03);
  transform: translateY(-4px) !important;
}
.metric-card::after {
  content: '';
  position: absolute; inset: 0;
  background: linear-gradient(135deg, rgba(0,212,255,0.04), transparent);
  opacity: 0; transition: opacity 0.3s;
}
.metric-card:hover::after { opacity: 1; }
.metric-card-icon {
  font-size: 18px; margin-bottom: 12px;
  opacity: 0.7;
}
.metric-card-num {
  font-family: var(--font-display);
  font-size: 26px;
  font-weight: 700;
  color: var(--cyan);
  letter-spacing: -0.02em;
}
.metric-card-label {
  font-family: var(--font-mono);
  font-size: 10px;
  letter-spacing: 0.15em;
  color: var(--text-secondary);
  text-transform: uppercase;
  margin-top: 4px;
}

/* SKILLS */
.skills-categories {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}
.skill-module {
  background: var(--glass);
  border: 1px solid var(--glass-border);
  padding: 28px;
  position: relative;
  overflow: hidden;
  cursor: default;
  transition: all 0.35s cubic-bezier(0.4,0,0.2,1);
  backdrop-filter: blur(16px);
}
.skill-module::before {
  content: '';
  position: absolute; top: 0; left: 0; right: 0;
  height: 2px;
  background: linear-gradient(90deg, transparent, var(--cyan), transparent);
  transform: scaleX(0);
  transition: transform 0.4s;
}
.skill-module:hover::before { transform: scaleX(1); }
.skill-module:hover {
  border-color: var(--glass-border-hover);
  box-shadow: 0 8px 40px rgba(0,212,255,0.12), 0 0 0 1px rgba(0,212,255,0.08);
  transform: translateY(-6px);
}
.skill-module-header {
  display: flex; align-items: center; gap: 12px;
  margin-bottom: 20px;
}
.skill-module-icon {
  width: 36px; height: 36px;
  background: linear-gradient(135deg, rgba(0,212,255,0.2), rgba(0,102,255,0.1));
  border: 1px solid rgba(0,212,255,0.2);
  display: flex; align-items: center; justify-content: center;
  font-size: 16px;
}
.skill-module-title {
  font-family: var(--font-mono);
  font-size: 11px;
  letter-spacing: 0.15em;
  color: var(--cyan);
  text-transform: uppercase;
}
.skill-tags {
  display: flex; flex-wrap: wrap; gap: 6px;
}
.skill-tag {
  font-family: var(--font-mono);
  font-size: 10px;
  letter-spacing: 0.08em;
  color: var(--text-secondary);
  background: rgba(0,212,255,0.05);
  border: 1px solid rgba(0,212,255,0.1);
  padding: 4px 10px;
  transition: all 0.2s;
}
.skill-module:hover .skill-tag {
  background: rgba(0,212,255,0.08);
  border-color: rgba(0,212,255,0.2);
  color: var(--text-primary);
}

/* EXPERIENCE */
.timeline {
  position: relative;
  padding-left: 32px;
}
.timeline::before {
  content: '';
  position: absolute; left: 0; top: 0; bottom: 0;
  width: 1px;
  background: linear-gradient(180deg, var(--cyan), rgba(0,212,255,0.1), transparent);
}
.timeline-item {
  position: relative;
  margin-bottom: 40px;
  opacity: 0;
  transform: translateX(-20px);
  transition: all 0.6s cubic-bezier(0.4,0,0.2,1);
}
.timeline-item.visible {
  opacity: 1;
  transform: translateX(0);
}
.timeline-dot {
  position: absolute; left: -39px; top: 28px;
  width: 14px; height: 14px;
  background: var(--bg-primary);
  border: 2px solid var(--cyan);
  border-radius: 50%;
  box-shadow: 0 0 12px var(--cyan-glow);
  transition: all 0.3s;
}
.timeline-item:hover .timeline-dot {
  background: var(--cyan);
  box-shadow: 0 0 20px var(--cyan);
}
.exp-card {
  background: var(--glass);
  border: 1px solid var(--glass-border);
  padding: 32px;
  backdrop-filter: blur(16px);
  transition: all 0.35s;
  position: relative; overflow: hidden;
}
.exp-card::before {
  content: '';
  position: absolute; left: 0; top: 0; bottom: 0;
  width: 3px;
  background: linear-gradient(180deg, var(--cyan), rgba(0,102,255,0.5));
  opacity: 0; transition: opacity 0.3s;
}
.exp-card:hover::before { opacity: 1; }
.exp-card:hover {
  border-color: var(--glass-border-hover);
  box-shadow: 0 8px 48px rgba(0,212,255,0.1);
  transform: translateX(6px);
}
.exp-header {
  display: flex; align-items: flex-start;
  justify-content: space-between;
  margin-bottom: 8px; gap: 20px;
}
.exp-role {
  font-family: var(--font-display);
  font-size: 18px;
  font-weight: 600;
  color: var(--text-primary);
}
.exp-period {
  font-family: var(--font-mono);
  font-size: 10px;
  letter-spacing: 0.15em;
  color: var(--cyan);
  white-space: nowrap;
  background: rgba(0,212,255,0.08);
  border: 1px solid rgba(0,212,255,0.15);
  padding: 4px 12px;
  flex-shrink: 0;
}
.exp-company {
  font-family: var(--font-mono);
  font-size: 12px;
  letter-spacing: 0.1em;
  color: var(--silver);
  margin-bottom: 20px;
}
.exp-points {
  list-style: none;
  display: flex; flex-direction: column; gap: 10px;
}
.exp-points li {
  font-size: 14px;
  color: var(--text-secondary);
  line-height: 1.65;
  padding-left: 16px;
  position: relative;
  font-weight: 300;
}
.exp-points li::before {
  content: '▸';
  position: absolute; left: 0;
  color: var(--cyan);
  font-size: 10px;
  top: 4px;
}
.exp-tags {
  display: flex; flex-wrap: wrap; gap: 6px;
  margin-top: 20px;
  padding-top: 20px;
  border-top: 1px solid rgba(0,212,255,0.06);
}
.exp-tag {
  font-family: var(--font-mono);
  font-size: 9px;
  letter-spacing: 0.12em;
  color: var(--text-muted);
  background: rgba(255,255,255,0.02);
  border: 1px solid rgba(255,255,255,0.05);
  padding: 3px 9px;
}

/* AI PROJECTS */
.projects-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}
.project-card {
  background: var(--glass);
  border: 1px solid var(--glass-border);
  padding: 28px;
  position: relative; overflow: hidden;
  backdrop-filter: blur(16px);
  cursor: default;
  transition: all 0.4s cubic-bezier(0.4,0,0.2,1);
}
.project-card:hover {
  border-color: var(--glass-border-hover);
  box-shadow: 0 16px 48px rgba(0,212,255,0.14);
  transform: translateY(-8px) scale(1.01);
}
.project-card::after {
  content: '';
  position: absolute; inset: 0;
  background: linear-gradient(135deg, rgba(0,212,255,0.06), rgba(0,102,255,0.03));
  opacity: 0; transition: opacity 0.4s;
}
.project-card:hover::after { opacity: 1; }
.project-num {
  font-family: var(--font-mono);
  font-size: 10px;
  letter-spacing: 0.2em;
  color: var(--text-muted);
  margin-bottom: 20px;
}
.project-icon-wrap {
  width: 48px; height: 48px;
  background: linear-gradient(135deg, rgba(0,212,255,0.15), rgba(0,102,255,0.08));
  border: 1px solid rgba(0,212,255,0.2);
  display: flex; align-items: center; justify-content: center;
  font-size: 22px; margin-bottom: 20px;
  transition: all 0.3s;
}
.project-card:hover .project-icon-wrap {
  box-shadow: 0 0 24px rgba(0,212,255,0.25);
  border-color: rgba(0,212,255,0.4);
}
.project-title {
  font-family: var(--font-display);
  font-size: 17px;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 12px;
  line-height: 1.3;
}
.project-desc {
  font-size: 13px;
  color: var(--text-secondary);
  line-height: 1.7;
  font-weight: 300;
}
.project-result {
  display: flex; align-items: center; gap: 8px;
  margin-top: 20px;
  padding-top: 16px;
  border-top: 1px solid rgba(0,212,255,0.06);
}
.project-result-num {
  font-family: var(--font-display);
  font-size: 20px;
  font-weight: 700;
  color: var(--cyan);
}
.project-result-label {
  font-family: var(--font-mono);
  font-size: 10px;
  color: var(--text-muted);
  letter-spacing: 0.1em;
}

/* EDUCATION */
.edu-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;
  margin-bottom: 32px;
}
.edu-card, .cert-card {
  background: var(--glass);
  border: 1px solid var(--glass-border);
  padding: 28px;
  position: relative; overflow: hidden;
  backdrop-filter: blur(16px);
  transition: all 0.3s;
}
.edu-card:hover, .cert-card:hover {
  border-color: var(--glass-border-hover);
  box-shadow: 0 8px 32px rgba(0,212,255,0.1);
}
.edu-card::before {
  content: '';
  position: absolute; top: 0; left: 0; right: 0;
  height: 2px;
  background: linear-gradient(90deg, var(--cyan), transparent);
}
.edu-degree {
  font-family: var(--font-display);
  font-size: 16px;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 6px;
}
.edu-school {
  font-family: var(--font-mono);
  font-size: 11px;
  letter-spacing: 0.1em;
  color: var(--silver);
  margin-bottom: 12px;
}
.edu-gpa {
  font-family: var(--font-display);
  font-size: 22px;
  font-weight: 700;
  color: var(--cyan);
}
.edu-note {
  font-size: 12px;
  color: var(--text-secondary);
  line-height: 1.6;
  margin-top: 10px;
  font-style: italic;
  font-weight: 300;
}
.certs-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
}
.cert-card {
  padding: 20px 24px;
}
.cert-title {
  font-family: var(--font-body);
  font-size: 13px;
  font-weight: 500;
  color: var(--text-primary);
  margin-bottom: 6px;
}
.cert-issuer {
  font-family: var(--font-mono);
  font-size: 10px;
  letter-spacing: 0.1em;
  color: var(--silver);
}
.cert-year {
  font-family: var(--font-mono);
  font-size: 10px;
  color: var(--cyan);
  margin-top: 8px;
}

/* CONTACT */
#contact { background: linear-gradient(180deg, transparent, rgba(0,212,255,0.015), transparent); }
.contact-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 48px;
  align-items: start;
}
.contact-info p {
  font-size: 15px;
  color: var(--text-secondary);
  line-height: 1.8;
  margin-bottom: 36px;
  font-weight: 300;
}
.contact-items { display: flex; flex-direction: column; gap: 16px; }
.contact-item {
  display: flex; align-items: center; gap: 14px;
  padding: 16px 20px;
  background: var(--glass);
  border: 1px solid var(--glass-border);
  transition: all 0.2s;
}
.contact-item:hover {
  border-color: rgba(0,212,255,0.25);
  background: rgba(0,212,255,0.04);
}
.contact-item-icon {
  width: 32px; height: 32px;
  background: rgba(0,212,255,0.1);
  display: flex; align-items: center; justify-content: center;
  font-size: 14px; color: var(--cyan);
  flex-shrink: 0;
}
.contact-item-content label {
  font-family: var(--font-mono);
  font-size: 9px;
  letter-spacing: 0.2em;
  color: var(--text-muted);
  text-transform: uppercase;
  display: block;
}
.contact-item-content span {
  font-size: 13px;
  color: var(--text-primary);
}
.contact-form { display: flex; flex-direction: column; gap: 16px; }
.form-group { display: flex; flex-direction: column; gap: 8px; }
.form-label {
  font-family: var(--font-mono);
  font-size: 10px;
  letter-spacing: 0.2em;
  color: var(--text-secondary);
  text-transform: uppercase;
}
.form-input, .form-textarea {
  background: rgba(0,212,255,0.03);
  border: 1px solid rgba(0,212,255,0.1);
  color: var(--text-primary);
  padding: 12px 16px;
  font-family: var(--font-body);
  font-size: 14px;
  outline: none;
  transition: all 0.2s;
  width: 100%;
}
.form-input:focus, .form-textarea:focus {
  border-color: rgba(0,212,255,0.4);
  box-shadow: 0 0 20px rgba(0,212,255,0.08);
  background: rgba(0,212,255,0.05);
}
.form-textarea { min-height: 120px; resize: vertical; }
.form-submit {
  font-family: var(--font-mono);
  font-size: 12px;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--cyan);
  background: linear-gradient(135deg, rgba(0,212,255,0.1), rgba(0,102,255,0.05));
  border: 1px solid rgba(0,212,255,0.3);
  padding: 14px 32px;
  cursor: pointer;
  transition: all 0.25s;
  align-self: flex-start;
}
.form-submit:hover {
  background: linear-gradient(135deg, rgba(0,212,255,0.2), rgba(0,102,255,0.12));
  border-color: var(--cyan);
  box-shadow: 0 0 30px rgba(0,212,255,0.25);
}

/* FOOTER */
footer {
  position: relative; z-index: 1;
  padding: 40px;
  border-top: 1px solid rgba(0,212,255,0.06);
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.footer-logo {
  font-family: var(--font-mono);
  font-size: 11px;
  letter-spacing: 0.3em;
  color: var(--text-muted);
  text-transform: uppercase;
}
.footer-copy {
  font-family: var(--font-mono);
  font-size: 10px;
  color: var(--text-muted);
  letter-spacing: 0.1em;
}
.footer-links {
  display: flex; gap: 24px;
}
.footer-links a {
  font-family: var(--font-mono);
  font-size: 10px;
  letter-spacing: 0.15em;
  color: var(--text-muted);
  text-decoration: none;
  text-transform: uppercase;
  transition: color 0.2s;
}
.footer-links a:hover { color: var(--cyan); }

/* SCROLL REVEAL */
.reveal {
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.7s cubic-bezier(0.4,0,0.2,1), transform 0.7s cubic-bezier(0.4,0,0.2,1);
}
.reveal.visible {
  opacity: 1;
  transform: translateY(0);
}

/* GLITCH EFFECT ON HOVER */
.glitch-text {
  position: relative;
}
.glitch-text::before, .glitch-text::after {
  content: attr(data-text);
  position: absolute; inset: 0;
  opacity: 0;
  transition: opacity 0.1s;
}
.glitch-text:hover::before {
  opacity: 0.8;
  color: var(--cyan);
  clip-path: polygon(0 20%, 100% 20%, 100% 40%, 0 40%);
  transform: translate(-2px, 0);
}
.glitch-text:hover::after {
  opacity: 0.8;
  color: #ff00ff;
  clip-path: polygon(0 60%, 100% 60%, 100% 80%, 0 80%);
  transform: translate(2px, 0);
}

/* HOLOGRAPHIC SCAN BADGE */
.holo-badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  font-family: var(--font-mono);
  font-size: 10px;
  letter-spacing: 0.2em;
  color: var(--cyan);
  background: rgba(0,212,255,0.06);
  border: 1px solid rgba(0,212,255,0.2);
  padding: 6px 14px;
  text-transform: uppercase;
  margin-bottom: 12px;
}
.holo-badge::before {
  content: '◈';
  animation: spin 3s linear infinite;
  display: inline-block;
}
@keyframes spin { to { transform: rotate(360deg); } }

/* STATUS BAR */
.status-bar {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-bottom: 48px;
  flex-wrap: wrap;
}
.status-item {
  font-family: var(--font-mono);
  font-size: 10px;
  letter-spacing: 0.15em;
  color: var(--text-muted);
  display: flex; align-items: center; gap: 6px;
  text-transform: uppercase;
}
.status-item::before {
  content: '';
  width: 5px; height: 5px;
  background: var(--cyan);
  border-radius: 50%;
  box-shadow: 0 0 6px var(--cyan);
}
.status-sep {
  font-family: var(--font-mono);
  font-size: 10px;
  color: var(--text-muted);
}

/* MOBILE NAV TOGGLE */
.nav-toggle {
  display: none;
  flex-direction: column; gap: 5px;
  cursor: pointer;
  padding: 8px;
}
.nav-toggle span {
  width: 22px; height: 1px;
  background: var(--cyan);
  transition: all 0.3s;
}

/* RESPONSIVE */
@media (max-width: 900px) {
  .nav-links { display: none; }
  .nav-toggle { display: flex; }
  .about-grid { grid-template-columns: 1fr; }
  .skills-categories { grid-template-columns: repeat(2, 1fr); }
  .projects-grid { grid-template-columns: repeat(2, 1fr); }
  .contact-grid { grid-template-columns: 1fr; }
  .edu-grid { grid-template-columns: 1fr; }
  .certs-grid { grid-template-columns: 1fr 1fr; }
  footer { flex-direction: column; gap: 20px; text-align: center; }
  .hero-stats { gap: 16px; }
}
@media (max-width: 600px) {
  nav { padding: 16px 24px; }
  .section-wrap { padding: 80px 24px; }
  .skills-categories { grid-template-columns: 1fr; }
  .projects-grid { grid-template-columns: 1fr; }
  .certs-grid { grid-template-columns: 1fr; }
  .hero-name { font-size: 32px; }
  .metrics-grid { grid-template-columns: 1fr 1fr; }
  .status-bar { display: none; }
  .section-label { display: none; }
  .section-header { flex-direction: column; align-items: flex-start; gap: 8px; }
  .section-label { writing-mode: horizontal-tb; transform: none; }
}
</style>
</head>
<body>

<!-- CURSOR -->
<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursor-ring"></div>

<!-- LOADER -->
<div id="loader">
  <div class="loader-logo">SYS.BOOT — VA.OS v3.1</div>
  <div class="loader-bar-wrap"><div class="loader-bar"></div></div>
  <div class="loader-text">Initializing Vyta Andri Interface...</div>
</div>

<!-- BACKGROUND -->
<canvas id="particles-canvas"></canvas>
<div class="grid-overlay"></div>

<!-- NAVIGATION -->
<nav id="navbar">
  <div class="nav-logo">VYTA.AI</div>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#experience">Experience</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#education">Education</a></li>
  </ul>
  <a href="#contact" class="nav-cta">Connect</a>
  <div class="nav-toggle" id="nav-toggle">
    <span></span><span></span><span></span>
  </div>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="holo-orb orb-1"></div>
  <div class="holo-orb orb-2"></div>
  <div class="holo-orb orb-3"></div>
  <div class="scan-line"></div>

  <div class="hero-eyebrow">Executive Virtual Assistant</div>

  <h1 class="hero-name glitch-text" data-text="VYTA ANDRI SETYO UTAMI">
    <span>VYTA ANDRI</span><br>SETYO UTAMI
  </h1>
  <p class="hero-sub">AI-Powered Executive Operations Specialist · Remote-Native · UTC+7</p>

  <div class="hero-btns">
    <a href="#experience" class="btn-primary">View Portfolio</a>
    <a href="#contact" class="btn-secondary">Contact Me</a>
  </div>

  <div class="hero-stats">
    <div class="hero-stat">
      <div class="stat-num">6+</div>
      <div class="stat-label">Years Experience</div>
    </div>
    <div class="hero-stat">
      <div class="stat-num">100%</div>
      <div class="stat-label">Payroll Accuracy</div>
    </div>
    <div class="hero-stat">
      <div class="stat-num">2–3×</div>
      <div class="stat-label">Revenue Scaled</div>
    </div>
    <div class="hero-stat">
      <div class="stat-num">809</div>
      <div class="stat-label">SKUs Managed</div>
    </div>
    <div class="hero-stat">
      <div class="stat-num">0</div>
      <div class="stat-label">Missed Deadlines</div>
    </div>
  </div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="section-wrap">
    <div class="section-header reveal">
      <span class="section-label">01 — Profile</span>
      <div>
        <h2 class="section-title">Intelligent <em>Operations.</em><br>Remote Precision.</h2>
        <div class="section-divider"></div>
      </div>
    </div>

    <div class="about-grid">
      <div class="about-text reveal">
        <div class="status-bar">
          <span class="status-item">Available Immediately</span>
          <span class="status-sep">·</span>
          <span class="status-item">Remote-Native</span>
          <span class="status-sep">·</span>
          <span class="status-item">AI-Certified 2026</span>
        </div>
        <p>Detail-obsessed Executive Virtual Assistant with <strong>6+ years</strong> supporting business operations across e-commerce, F&B, logistics, and printing. I make executives and founders more effective by owning their operational backbone.</p>
        <div class="about-highlight">"I build systems that don't depend on constant oversight — async-first, proactive, and reliable across time zones."</div>
        <p>As co-founder of a gelato café, I built operations, teams, and B2B partnerships from scratch. Across two printing companies, I owned invoicing, payroll, scheduling, and financial reporting for 8–11 person teams — error-free, on time, every cycle.</p>
        <p>At Fashiondeals, I ran a 14-month solo remote engagement scaling revenue <strong>2–3× through systematic process design</strong>. Certified in AI + n8n Workflow Automation (April 2026), I leverage AI tools daily to reduce turnaround time and build high-efficiency systems.</p>
      </div>

      <div class="metrics-grid reveal">
        <div class="metric-card">
          <div class="metric-card-icon">🎯</div>
          <div class="metric-card-num">6+</div>
          <div class="metric-card-label">Industries Supported</div>
        </div>
        <div class="metric-card">
          <div class="metric-card-icon">💡</div>
          <div class="metric-card-num">2–3×</div>
          <div class="metric-card-label">Revenue Growth</div>
        </div>
        <div class="metric-card">
          <div class="metric-card-icon">⚡</div>
          <div class="metric-card-num">30%</div>
          <div class="metric-card-label">Error Reduction</div>
        </div>
        <div class="metric-card">
          <div class="metric-card-icon">🌐</div>
          <div class="metric-card-num">UTC+7</div>
          <div class="metric-card-label">Timezone Flexible</div>
        </div>
        <div class="metric-card">
          <div class="metric-card-icon">📊</div>
          <div class="metric-card-num">657+</div>
          <div class="metric-card-label">Orders Managed</div>
        </div>
        <div class="metric-card">
          <div class="metric-card-icon">🤖</div>
          <div class="metric-card-num">n8n</div>
          <div class="metric-card-label">AI Automation Cert.</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- SKILLS -->
<section id="skills">
  <div class="section-wrap">
    <div class="section-header reveal">
      <span class="section-label">02 — Capabilities</span>
      <div>
        <h2 class="section-title">Core <em>Skill Modules.</em></h2>
        <div class="section-divider"></div>
      </div>
    </div>

    <div class="skills-categories">
      <div class="skill-module reveal">
        <div class="skill-module-header">
          <div class="skill-module-icon">🗂️</div>
          <div class="skill-module-title">Executive Support</div>
        </div>
        <div class="skill-tags">
          <span class="skill-tag">Calendar Management</span>
          <span class="skill-tag">Email Triage</span>
          <span class="skill-tag">Travel Coordination</span>
          <span class="skill-tag">Meeting Prep & Notes</span>
          <span class="skill-tag">Document Creation</span>
          <span class="skill-tag">Stakeholder Comms</span>
        </div>
      </div>
      <div class="skill-module reveal">
        <div class="skill-module-header">
          <div class="skill-module-icon">⚙️</div>
          <div class="skill-module-title">Operations Management</div>
        </div>
        <div class="skill-tags">
          <span class="skill-tag">SOP Creation</span>
          <span class="skill-tag">Process Documentation</span>
          <span class="skill-tag">Invoice & PO Tracking</span>
          <span class="skill-tag">Payroll Processing</span>
          <span class="skill-tag">Vendor Coordination</span>
          <span class="skill-tag">Inventory Management</span>
        </div>
      </div>
      <div class="skill-module reveal">
        <div class="skill-module-header">
          <div class="skill-module-icon">🤖</div>
          <div class="skill-module-title">AI & Automation</div>
        </div>
        <div class="skill-tags">
          <span class="skill-tag">n8n Automation</span>
          <span class="skill-tag">AI Content Gen</span>
          <span class="skill-tag">AI Image Tools</span>
          <span class="skill-tag">Automated Reporting</span>
          <span class="skill-tag">Data Pipelines</span>
          <span class="skill-tag">Workflow Design</span>
        </div>
      </div>
      <div class="skill-module reveal">
        <div class="skill-module-header">
          <div class="skill-module-icon">☁️</div>
          <div class="skill-module-title">Remote Collaboration</div>
        </div>
        <div class="skill-tags">
          <span class="skill-tag">Google Workspace</span>
          <span class="skill-tag">Microsoft 365</span>
          <span class="skill-tag">Slack</span>
          <span class="skill-tag">MS Teams</span>
          <span class="skill-tag">Zoom</span>
          <span class="skill-tag">Trello / Async-First</span>
        </div>
      </div>
      <div class="skill-module reveal">
        <div class="skill-module-header">
          <div class="skill-module-icon">📈</div>
          <div class="skill-module-title">Reporting & Analytics</div>
        </div>
        <div class="skill-tags">
          <span class="skill-tag">Financial Reporting</span>
          <span class="skill-tag">P&L Management</span>
          <span class="skill-tag">Google Data Studio</span>
          <span class="skill-tag">Excel Pivot Tables</span>
          <span class="skill-tag">Dashboard Design</span>
          <span class="skill-tag">KPI Tracking</span>
        </div>
      </div>
      <div class="skill-module reveal">
        <div class="skill-module-header">
          <div class="skill-module-icon">🏢</div>
          <div class="skill-module-title">Business Systems</div>
        </div>
        <div class="skill-tags">
          <span class="skill-tag">ERP Systems</span>
          <span class="skill-tag">E-Commerce Ops</span>
          <span class="skill-tag">Marketplace Strategy</span>
          <span class="skill-tag">Live Streaming</span>
          <span class="skill-tag">B2B Partnerships</span>
          <span class="skill-tag">Tax & Accounting</span>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- EXPERIENCE -->
<section id="experience">
  <div class="section-wrap">
    <div class="section-header reveal">
      <span class="section-label">03 — Career Log</span>
      <div>
        <h2 class="section-title">Professional <em>Experience.</em></h2>
        <div class="section-divider"></div>
      </div>
    </div>

    <div class="timeline">

      <div class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="exp-card reveal">
          <div class="exp-header">
            <div>
              <div class="holo-badge">Active Engagement</div>
              <div class="exp-role">Remote Operations & E-Commerce Coordinator</div>
            </div>
            <div class="exp-period">Jan 2025 – Mar 2026</div>
          </div>
          <div class="exp-company">Fashiondeals · Jakarta Barat · Fully Remote</div>
          <ul class="exp-points">
            <li>Managed full operational cycle solo across 809 SKUs and 657+ orders — inventory, logistics, analytics, and promotional strategy without in-person oversight.</li>
            <li>Redesigned promotional calendar, pricing structure, and live-stream schedule, delivering consistent 2–3× monthly revenue growth over 14 months with zero headcount increase.</li>
            <li>Built standardized digital SOPs for all marketplace workflows, enabling platform-wide consistency and reducing onboarding friction.</li>
            <li>Eliminated customer complaints related to fulfillment within 3 months by liaising with 3rd-party logistics providers on delivery scheduling and issue resolution.</li>
            <li>Produced weekly analytics reports from Shopee Dashboard translating raw data into executive-ready summaries with clear action recommendations.</li>
          </ul>
          <div class="exp-tags">
            <span class="exp-tag">E-Commerce</span><span class="exp-tag">Shopee Dashboard</span>
            <span class="exp-tag">SOP Design</span><span class="exp-tag">Async Operations</span>
            <span class="exp-tag">Logistics</span><span class="exp-tag">Revenue Strategy</span>
          </div>
        </div>
      </div>

      <div class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="exp-card reveal">
          <div class="exp-header">
            <div>
              <div class="holo-badge">Founder Track</div>
              <div class="exp-role">Co-Founder & Operations Manager</div>
            </div>
            <div class="exp-period">Dec 2021 – Jun 2023</div>
          </div>
          <div class="exp-company">Velluto Gelato · Jakarta Barat</div>
          <ul class="exp-points">
            <li>Functioned as executive right-hand through full launch lifecycle — managing contractors, vendors, licensing, staffing, and financial setup simultaneously for an on-time opening.</li>
            <li>Managed daily P&L records, procurement, and supplier negotiations, maintaining >95% financial accuracy across all monthly reporting cycles.</li>
            <li>Organized and led a 6-person team from hire to performance management, creating role documentation and accountability systems that improved efficiency by 20% in Q1.</li>
            <li>Secured 2 new revenue channels (expo tent & hotel supply) through B2B outreach and partnership negotiations with hotels and event organizers.</li>
            <li>Designed expiry monitoring and procurement controls that cut raw material waste 15–25%, freeing up budget for growth reinvestment.</li>
          </ul>
          <div class="exp-tags">
            <span class="exp-tag">P&L Management</span><span class="exp-tag">Team Leadership</span>
            <span class="exp-tag">Vendor Relations</span><span class="exp-tag">B2B</span>
            <span class="exp-tag">F&B Operations</span><span class="exp-tag">Launch Management</span>
          </div>
        </div>
      </div>

      <div class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="exp-card reveal">
          <div class="exp-header">
            <div>
              <div class="holo-badge">Operations</div>
              <div class="exp-role">Project Coordinator — Admin & Operations</div>
            </div>
            <div class="exp-period">Jun 2023 – Sep 2024</div>
          </div>
          <div class="exp-company">PT Prima Mandiri Kencana · Jakarta Barat</div>
          <ul class="exp-points">
            <li>Owned the full document lifecycle for a mid-size printing operation — POs, quotations, work orders, invoices, and delivery records — ensuring 100% on-time billing with zero cash flow gaps.</li>
            <li>Built monthly PPn/Non-PPn financial reports in Excel, turning raw transaction data into clear management summaries for planning and tax compliance.</li>
            <li>Coordinated production scheduling across 3+ daily runs, reducing delays by 10% through proactive issue identification.</li>
            <li>Maintained ~80% on-time delivery rate across all client orders through systematic scheduling and documentation controls.</li>
          </ul>
          <div class="exp-tags">
            <span class="exp-tag">Document Control</span><span class="exp-tag">Financial Reporting</span>
            <span class="exp-tag">Production Scheduling</span><span class="exp-tag">Excel</span>
            <span class="exp-tag">Tax Compliance</span>
          </div>
        </div>
      </div>

      <div class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="exp-card reveal">
          <div class="exp-header">
            <div>
              <div class="holo-badge">Foundation</div>
              <div class="exp-role">Warehouse & Operations Administrator</div>
            </div>
            <div class="exp-period">Feb 2020 – Dec 2021</div>
          </div>
          <div class="exp-company">CV Chandra Jaya · Jakarta Barat</div>
          <ul class="exp-points">
            <li>Processed payroll for 11 employees with 100% accuracy every billing cycle — zero errors, zero revisions across the full 22-month tenure.</li>
            <li>Redesigned financial tracking process, reducing monthly report discrepancy from >5% to <2%, creating a reliable baseline for management decision-making.</li>
            <li>Managed 15+ daily delivery orders maintaining a 95% on-time rate while coordinating across warehouse, production, and logistics teams simultaneously.</li>
            <li>Cut stock input errors by 30% through systematic inventory monitoring, keeping warehouse discrepancy consistently below 3%.</li>
          </ul>
          <div class="exp-tags">
            <span class="exp-tag">Payroll</span><span class="exp-tag">Inventory</span>
            <span class="exp-tag">Logistics</span><span class="exp-tag">Financial Tracking</span>
            <span class="exp-tag">Warehouse Ops</span>
          </div>
        </div>
      </div>

    </div>
  </div>
</section>

<!-- AI PROJECTS -->
<section id="projects">
  <div class="section-wrap">
    <div class="section-header reveal">
      <span class="section-label">04 — Systems</span>
      <div>
        <h2 class="section-title">AI & Business <em>Projects.</em></h2>
        <div class="section-divider"></div>
      </div>
    </div>

    <div class="projects-grid">
      <div class="project-card reveal">
        <div class="project-num">PRJ.001</div>
        <div class="project-icon-wrap">⚡</div>
        <div class="project-title">n8n Workflow Automation System</div>
        <div class="project-desc">Built automated reporting and data pipeline workflows using n8n, reducing manual turnaround time and eliminating repetitive task overhead for remote operations.</div>
        <div class="project-result">
          <div class="project-result-num">↑ 40%</div>
          <div class="project-result-label">Efficiency Gain</div>
        </div>
      </div>

      <div class="project-card reveal">
        <div class="project-num">PRJ.002</div>
        <div class="project-icon-wrap">📋</div>
        <div class="project-title">E-Commerce SOP Architecture</div>
        <div class="project-desc">Designed and implemented a complete digital SOP library for marketplace operations across 809 SKUs — enabling consistent execution and rapid team onboarding without oversight.</div>
        <div class="project-result">
          <div class="project-result-num">809</div>
          <div class="project-result-label">SKUs Systematized</div>
        </div>
      </div>

      <div class="project-card reveal">
        <div class="project-num">PRJ.003</div>
        <div class="project-icon-wrap">📊</div>
        <div class="project-title">Executive Analytics Dashboard</div>
        <div class="project-desc">Created weekly analytics reporting system transforming raw Shopee data into executive-ready summaries with clear KPIs, trends, and action recommendations.</div>
        <div class="project-result">
          <div class="project-result-num">2–3×</div>
          <div class="project-result-label">Revenue Growth Tracked</div>
        </div>
      </div>

      <div class="project-card reveal">
        <div class="project-num">PRJ.004</div>
        <div class="project-icon-wrap">🏪</div>
        <div class="project-title">Café Launch Operations System</div>
        <div class="project-desc">Architected end-to-end operational framework for gelato café launch — vendor management, team structure, P&L controls, procurement systems, and B2B channel development.</div>
        <div class="project-result">
          <div class="project-result-num">+2</div>
          <div class="project-result-label">Revenue Channels Opened</div>
        </div>
      </div>

      <div class="project-card reveal">
        <div class="project-num">PRJ.005</div>
        <div class="project-icon-wrap">💰</div>
        <div class="project-title">Financial Accuracy System</div>
        <div class="project-desc">Rebuilt financial tracking process for printing operations, reducing monthly discrepancy from >5% to <2% and establishing reliable reporting baseline for management decisions.</div>
        <div class="project-result">
          <div class="project-result-num">100%</div>
          <div class="project-result-label">Payroll Accuracy</div>
        </div>
      </div>

      <div class="project-card reveal">
        <div class="project-num">PRJ.006</div>
        <div class="project-icon-wrap">🔗</div>
        <div class="project-title">Logistics Fulfillment Optimization</div>
        <div class="project-desc">Eliminated customer complaints related to fulfillment within 3 months by redesigning 3PL coordination workflows, delivery scheduling, and real-time issue resolution protocols.</div>
        <div class="project-result">
          <div class="project-result-num">95%</div>
          <div class="project-result-label">On-Time Delivery</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- EDUCATION -->
<section id="education">
  <div class="section-wrap">
    <div class="section-header reveal">
      <span class="section-label">05 — Credentials</span>
      <div>
        <h2 class="section-title">Education & <em>Certifications.</em></h2>
        <div class="section-divider"></div>
      </div>
    </div>

    <div class="edu-grid reveal">
      <div class="edu-card">
        <div class="edu-degree">Master's Degree — Science Education</div>
        <div class="edu-school">Universitas Negeri Yogyakarta · 2019</div>
        <div class="edu-gpa">GPA 3.78 / 4.00</div>
        <p class="edu-note">Research in designing interactive learning media — developed transferable skills in process documentation, instructional system design, and structured knowledge delivery.</p>
      </div>
      <div class="edu-card">
        <div class="edu-degree">Bachelor's Degree — Biology Education</div>
        <div class="edu-school">Universitas Negeri Yogyakarta · 2016</div>
        <div class="edu-gpa">GPA 3.38 / 4.00</div>
        <p class="edu-note">Strong foundation in analytical thinking, research methodology, and systematic problem-solving — applied directly to operational and data-driven roles.</p>
      </div>
    </div>

    <div class="certs-grid">
      <div class="cert-card reveal">
        <div class="cert-title">Automating with AI + n8n</div>
        <div class="cert-issuer">MySkill</div>
        <div class="cert-year">April 2026 · ◈ Certified</div>
      </div>
      <div class="cert-card reveal">
        <div class="cert-title">Accounting & Taxation Bootcamp</div>
        <div class="cert-issuer">Kelas.com</div>
        <div class="cert-year">Jan 2025 · ◈ Certified</div>
      </div>
      <div class="cert-card reveal">
        <div class="cert-title">Microsoft Excel — Pivot Table & Formulas</div>
        <div class="cert-issuer">MySkill</div>
        <div class="cert-year">Dec–Jan 2025 · ◈ Certified</div>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="section-wrap">
    <div class="section-header reveal">
      <span class="section-label">06 — Connect</span>
      <div>
        <h2 class="section-title">Ready to <em>Collaborate.</em></h2>
        <div class="section-divider"></div>
      </div>
    </div>

    <div class="contact-grid">
      <div class="contact-info reveal">
        <p>Available immediately for executive virtual assistant and operations roles. Remote-native, async-first, and flexible across US, EU, and AU time zones. Let's build something efficient together.</p>
        <div class="contact-items">
          <div class="contact-item">
            <div class="contact-item-icon">📱</div>
            <div class="contact-item-content">
              <label>WhatsApp / Phone</label>
              <span>+62 8777 2457 414</span>
            </div>
          </div>
          <div class="contact-item">
            <div class="contact-item-icon">✉️</div>
            <div class="contact-item-content">
              <label>Email</label>
              <span>vytautami@gmail.com</span>
            </div>
          </div>
          <div class="contact-item">
            <div class="contact-item-icon">🌐</div>
            <div class="contact-item-content">
              <label>Location · Timezone</label>
              <span>Bekasi, Indonesia · UTC+7 (WIB)</span>
            </div>
          </div>
          <div class="contact-item">
            <div class="contact-item-icon">💼</div>
            <div class="contact-item-content">
              <label>LinkedIn</label>
              <span>linkedin.com/in/vytautami</span>
            </div>
          </div>
        </div>
      </div>

      <div class="contact-form reveal">
        <div class="form-group">
          <label class="form-label">Your Name</label>
          <input type="text" class="form-input" placeholder="John Smith">
        </div>
        <div class="form-group">
          <label class="form-label">Email Address</label>
          <input type="email" class="form-input" placeholder="john@company.com">
        </div>
        <div class="form-group">
          <label class="form-label">Subject</label>
          <input type="text" class="form-input" placeholder="Executive VA Opportunity">
        </div>
        <div class="form-group">
          <label class="form-label">Message</label>
          <textarea class="form-textarea" placeholder="Tell me about the role and what you're looking for..."></textarea>
        </div>
        <button class="form-submit" onclick="handleSend(this)">▸ Send Message</button>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">VYTA.AI · © 2026</div>
  <div class="footer-copy">AI-Powered Executive Operations · Remote-Native · UTC+7</div>
  <div class="footer-links">
    <a href="mailto:vytautami@gmail.com">Email</a>
    <a href="tel:+6287772457414">Phone</a>
    <a href="#">LinkedIn</a>
    <a href="#">Portfolio</a>
  </div>
</footer>

<script>
// LOADER
window.addEventListener('load', () => {
  setTimeout(() => {
    document.getElementById('loader').classList.add('hidden');
  }, 2200);
});

// CUSTOM CURSOR
const cursor = document.getElementById('cursor');
const ring = document.getElementById('cursor-ring');
let mx = 0, my = 0, rx = 0, ry = 0;
document.addEventListener('mousemove', e => {
  mx = e.clientX; my = e.clientY;
  cursor.style.left = mx + 'px';
  cursor.style.top = my + 'px';
});
function animRing() {
  rx += (mx - rx) * 0.12;
  ry += (my - ry) * 0.12;
  ring.style.left = rx + 'px';
  ring.style.top = ry + 'px';
  requestAnimationFrame(animRing);
}
animRing();
document.querySelectorAll('a, button, .skill-module, .project-card, .exp-card, .metric-card').forEach(el => {
  el.addEventListener('mouseenter', () => {
    cursor.style.transform = 'translate(-50%,-50%) scale(2)';
    ring.style.width = '54px'; ring.style.height = '54px';
    ring.style.borderColor = 'rgba(0,212,255,0.8)';
  });
  el.addEventListener('mouseleave', () => {
    cursor.style.transform = 'translate(-50%,-50%) scale(1)';
    ring.style.width = '36px'; ring.style.height = '36px';
    ring.style.borderColor = 'rgba(0,212,255,0.5)';
  });
});

// PARTICLES
const canvas = document.getElementById('particles-canvas');
const ctx = canvas.getContext('2d');
let W = canvas.width = window.innerWidth;
let H = canvas.height = window.innerHeight;
window.addEventListener('resize', () => {
  W = canvas.width = window.innerWidth;
  H = canvas.height = window.innerHeight;
});
const dots = Array.from({length: 90}, () => ({
  x: Math.random() * W,
  y: Math.random() * H,
  r: Math.random() * 1.2 + 0.3,
  vx: (Math.random() - 0.5) * 0.25,
  vy: (Math.random() - 0.5) * 0.25,
  alpha: Math.random() * 0.5 + 0.1
}));
function drawParticles() {
  ctx.clearRect(0, 0, W, H);
  dots.forEach(d => {
    d.x += d.vx; d.y += d.vy;
    if (d.x < 0) d.x = W; if (d.x > W) d.x = 0;
    if (d.y < 0) d.y = H; if (d.y > H) d.y = 0;
    ctx.beginPath();
    ctx.arc(d.x, d.y, d.r, 0, Math.PI*2);
    ctx.fillStyle = `rgba(0,212,255,${d.alpha})`;
    ctx.fill();
  });
  // Lines between close dots
  for (let i = 0; i < dots.length; i++) {
    for (let j = i+1; j < dots.length; j++) {
      const dx = dots[i].x - dots[j].x;
      const dy = dots[i].y - dots[j].y;
      const dist = Math.sqrt(dx*dx + dy*dy);
      if (dist < 130) {
        ctx.beginPath();
        ctx.strokeStyle = `rgba(0,212,255,${0.06 * (1 - dist/130)})`;
        ctx.lineWidth = 0.5;
        ctx.moveTo(dots[i].x, dots[i].y);
        ctx.lineTo(dots[j].x, dots[j].y);
        ctx.stroke();
      }
    }
  }
  requestAnimationFrame(drawParticles);
}
drawParticles();

// SCROLL REVEAL
const reveals = document.querySelectorAll('.reveal');
const timelineItems = document.querySelectorAll('.timeline-item');
const observer = new IntersectionObserver((entries) => {
  entries.forEach((entry, i) => {
    if (entry.isIntersecting) {
      setTimeout(() => {
        entry.target.classList.add('visible');
      }, 80 * (Array.from(reveals).indexOf(entry.target) % 4));
      observer.unobserve(entry.target);
    }
  });
}, { threshold: 0.1, rootMargin: '0px 0px -40px 0px' });
reveals.forEach(el => observer.observe(el));

const tlObserver = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('visible');
      tlObserver.unobserve(entry.target);
    }
  });
}, { threshold: 0.15 });
timelineItems.forEach(el => tlObserver.observe(el));

// MOUSE PARALLAX on hero orbs
document.addEventListener('mousemove', e => {
  const x = (e.clientX / window.innerWidth - 0.5) * 20;
  const y = (e.clientY / window.innerHeight - 0.5) * 20;
  document.querySelectorAll('.holo-orb').forEach((orb, i) => {
    const factor = (i + 1) * 0.4;
    orb.style.transform = `translate(${x * factor}px, ${y * factor}px)`;
  });
});

// 3D TILT on project cards
document.querySelectorAll('.project-card').forEach(card => {
  card.addEventListener('mousemove', e => {
    const rect = card.getBoundingClientRect();
    const x = (e.clientX - rect.left) / rect.width - 0.5;
    const y = (e.clientY - rect.top) / rect.height - 0.5;
    card.style.transform = `translateY(-8px) scale(1.01) rotateX(${-y * 6}deg) rotateY(${x * 6}deg)`;
  });
  card.addEventListener('mouseleave', () => {
    card.style.transform = '';
  });
});

// SEND BUTTON
function handleSend(btn) {
  const orig = btn.textContent;
  btn.textContent = '◈ Transmitting...';
  btn.style.opacity = '0.7';
  setTimeout(() => {
    btn.textContent = '✓ Message Queued';
    btn.style.color = '#00ff88';
    btn.style.borderColor = '#00ff88';
    setTimeout(() => {
      btn.textContent = orig;
      btn.style.color = '';
      btn.style.borderColor = '';
      btn.style.opacity = '';
    }, 2500);
  }, 1500);
}

// NAVBAR SCROLL
window.addEventListener('scroll', () => {
  const nav = document.getElementById('navbar');
  if (window.scrollY > 50) {
    nav.style.padding = '14px 40px';
  } else {
    nav.style.padding = '20px 40px';
  }
});

// ANIMATED COUNTER
function animateCounter(el, target, suffix = '') {
  let start = 0;
  const dur = 1600;
  const step = (timestamp) => {
    if (!start) start = timestamp;
    const progress = Math.min((timestamp - start) / dur, 1);
    const ease = 1 - Math.pow(1 - progress, 3);
    el.textContent = Math.round(ease * target) + suffix;
    if (progress < 1) requestAnimationFrame(step);
  };
  requestAnimationFrame(step);
}
const statNums = document.querySelectorAll('.stat-num');
const statObs = new IntersectionObserver(entries => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      const el = entry.target;
      const text = el.textContent;
      if (text === '6+') animateCounter(el, 6, '+');
      else if (text === '100%') animateCounter(el, 100, '%');
      else if (text === '809') animateCounter(el, 809, '');
      else if (text === '0') { el.textContent = '0'; }
      statObs.unobserve(el);
    }
  });
}, { threshold: 0.5 });
statNums.forEach(el => statObs.observe(el));
</script>
</body>
</html>
