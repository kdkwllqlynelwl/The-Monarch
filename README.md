<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>The Monarch | American Printing House</title>
  <meta
    name="description"
    content="The Monarch is a braille translation tool created to help people convert text into braille more efficiently and access information in a more inclusive way."
  />
  <style>
    :root {
      --navy: #0b1b2b;
      --navy-2: #132c40;
      --teal: #2a7f76;
      --gold: #d9b36a;
      --sand: #f5efe6;
      --white: #ffffff;
      --text: #1d2430;
      --muted: #5d6774;
      --border: rgba(19, 44, 64, 0.12);
      --shadow: 0 18px 45px rgba(11, 27, 43, 0.12);
      --max-width: 1200px;
    }

    * { box-sizing: border-box; }

    html { scroll-behavior: smooth; }

    body {
      margin: 0;
      font-family: Arial, Helvetica, sans-serif;
      background: var(--sand);
      color: var(--text);
      line-height: 1.6;
    }

    img { max-width: 100%; display: block; }

    a {
      color: inherit;
      text-decoration: none;
    }

    .container {
      width: min(var(--max-width), calc(100% - 32px));
      margin: 0 auto;
    }

    header {
      position: sticky;
      top: 0;
      z-index: 50;
      background: rgba(11, 27, 43, 0.9);
      backdrop-filter: blur(10px);
      border-bottom: 1px solid rgba(255,255,255,0.05);
    }

    .nav {
      display: flex;
      align-items: center;
      justify-content: space-between;
      min-height: 76px;
      gap: 20px;
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 12px;
      color: var(--white);
      font-weight: 700;
      letter-spacing: 0.04em;
      font-size: 1.1rem;
    }

    .brand-mark {
      width: 42px;
      height: 42px;
      border-radius: 50%;
      background: linear-gradient(135deg, var(--gold), #f4d89d);
      color: var(--navy);
      display: grid;
      place-items: center;
      font-weight: 900;
      font-size: 1.15rem;
    }

    .nav-links {
      display: flex;
      align-items: center;
      gap: 28px;
      color: rgba(255,255,255,0.88);
      font-size: 0.96rem;
    }

    .nav-links a:hover { color: var(--gold); }

    .button {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      padding: 0.9rem 1.4rem;
      border-radius: 999px;
      font-weight: 700;
      transition: 0.2s ease;
      border: 1px solid transparent;
      cursor: pointer;
    }

    .button.primary {
      background: var(--gold);
      color: var(--navy);
      box-shadow: var(--shadow);
    }

    .button.primary:hover {
      transform: translateY(-1px);
      filter: brightness(1.04);
    }

    .button.secondary {
      background: transparent;
      color: var(--white);
      border-color: rgba(255,255,255,0.2);
    }

    .button.secondary:hover {
      background: rgba(255,255,255,0.06);
    }

    .hero {
      background:
        linear-gradient(135deg, rgba(11, 27, 43, 0.94), rgba(19, 44, 64, 0.80)),
        radial-gradient(circle at top left, rgba(217,179,106,0.35), transparent 35%);
      color: var(--white);
      padding: 110px 0 92px;
    }

    .hero-grid {
      display: grid;
      grid-template-columns: 1.2fr 0.8fr;
      gap: 48px;
      align-items: center;
    }

    .eyebrow {
      display: inline-block;
      padding: 0.5rem 0.9rem;
      border-radius: 999px;
      background: rgba(255,255,255,0.08);
      border: 1px solid rgba(255,255,255,0.1);
      letter-spacing: 0.06em;
      font-size: 0.75rem;
      text-transform: uppercase;
      font-weight: 700;
      color: #e7e6dc;
    }

    h1, h2, h3 {
      margin: 0 0 1rem;
      line-height: 1.15;
      letter-spacing: -0.04em;
    }

    h1 {
      font-size: clamp(2.6rem, 5vw, 5rem);
      margin-top: 1.2rem;
    }

    .hero p {
      font-size: 1.08rem;
      color: rgba(255,255,255,0.85);
      margin: 0 0 2rem;
      max-width: 650px;
    }

    .hero-actions {
      display: flex;
      flex-wrap: wrap;
      gap: 16px;
      margin-bottom: 2rem;
    }

    .hero-stats {
      display: flex;
      flex-wrap: wrap;
      gap: 26px;
      margin-top: 1.2rem;
    }

    .hero-stat strong {
      display: block;
      font-size: 1.8rem;
      color: var(--gold);
      margin-bottom: 4px;
    }

    .hero-stat span {
      color: rgba(255,255,255,0.8);
      font-size: 0.92rem;
    }

    .hero-card {
      background: linear-gradient(180deg, rgba(255,255,255,0.08), rgba(255,255,255,0.02));
      border: 1px solid rgba(255,255,255,0.12);
      border-radius: 22px;
      padding: 24px;
      box-shadow: var(--shadow);
    }

    .monarch-panel {
      background: linear-gradient(135deg, rgba(217,179,106,0.15), rgba(42,127,118,0.12));
      border: 1px solid rgba(255,255,255,0.12);
      border-radius: 22px;
      padding: 24px;
    }

    .braille-block {
      background: var(--white);
      color: var(--navy);
      border-radius: 16px;
      padding: 20px;
      box-shadow: inset 0 0 0 1px rgba(11,27,43,0.08);
    }

    .braille-row {
      display: grid;
      grid-template-columns: repeat(5, 1fr);
      gap: 12px;
      margin-top: 12px;
    }

    .braille-dot {
      width: 22px;
      height: 22px;
      border-radius: 50%;
      background: var(--navy);
      margin: auto;
      opacity: 0.92;
    }

    .braille-dot.empty {
      background: rgba(11,27,43,0.14);
    }

    .section {
      padding: 90px 0;
    }

    .section-header {
      max-width: 760px;
      margin-bottom: 44px;
    }

    .section-header h2 {
      font-size: clamp(2.1rem, 4vw, 3.3rem);
      color: var(--navy);
    }

    .section-header p {
      margin: 0;
      color: var(--muted);
      font-size: 1.06rem;
    }

    .two-col {
      display: grid;
      grid-template-columns: 1.05fr 0.95fr;
      gap: 30px;
      align-items: center;
    }

    .feature-list {
      display: grid;
      gap: 18px;
    }

    .feature-item {
      background: rgba(255,255,255,0.8);
      border: 1px solid var(--border);
      border-radius: 18px;
      padding: 22px 22px 18px;
      box-shadow: 0 8px 24px rgba(8, 17, 29, 0.04);
    }

    .feature-item strong {
      display: block;
      color: var(--navy);
      font-size: 1.15rem;
      margin-bottom: 8px;
    }

    .feature-item p {
