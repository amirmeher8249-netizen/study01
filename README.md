<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Corporate Tax Planning | B.Com Sem-6 DSE-III</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@600;700&family=DM+Sans:wght@300;400;500;600&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #0b0e17;
    --bg2: #111827;
    --card: rgba(255,255,255,0.04);
    --border: rgba(240,180,41,0.2);
    --gold: #f0b429;
    --gold2: #fcd34d;
    --text: #e2e8f0;
    --muted: #94a3b8;
    --accent: #3b82f6;
    --green: #10b981;
    --red: #ef4444;
    --purple: #a78bfa;
    --radius: 14px;
  }
  * { margin:0; padding:0; box-sizing:border-box; }
  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    line-height: 1.7;
    min-height: 100vh;
  }

  /* HEADER */
  header {
    background: linear-gradient(135deg, #0b0e17 0%, #1a1040 50%, #0b0e17 100%);
    border-bottom: 1px solid var(--border);
    padding: 2.5rem 2rem 2rem;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  header::before {
    content: '';
    position: absolute;
    top: -80px; left: 50%;
    transform: translateX(-50%);
    width: 600px; height: 300px;
    background: radial-gradient(ellipse, rgba(240,180,41,0.12) 0%, transparent 70%);
    pointer-events: none;
  }
  .badge {
    display: inline-block;
    background: rgba(240,180,41,0.12);
    border: 1px solid rgba(240,180,41,0.35);
    color: var(--gold);
    font-size: 0.72rem;
    font-weight: 600;
    letter-spacing: 2px;
    text-transform: uppercase;
    padding: 0.3rem 1rem;
    border-radius: 50px;
    margin-bottom: 1rem;
  }
  header h1 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(1.6rem, 4vw, 2.6rem);
    color: #fff;
    margin-bottom: 0.4rem;
  }
  header h1 span { color: var(--gold); }
  header p {
    color: var(--muted);
    font-size: 0.9rem;
  }

  /* TABS */
  .tab-bar {
    display: flex;
    gap: 0.5rem;
    padding: 1rem 1.5rem;
    background: var(--bg2);
    border-bottom: 1px solid rgba(255,255,255,0.06);
    overflow-x: auto;
    scrollbar-width: none;
    position: sticky;
    top: 0;
    z-index: 100;
  }
  .tab-bar::-webkit-scrollbar { display: none; }
  .tab-btn {
    flex-shrink: 0;
    padding: 0.45rem 1.1rem;
    border-radius: 50px;
    border: 1px solid rgba(255,255,255,0.1);
    background: transparent;
    color: var(--muted);
    font-family: 'DM Sans', sans-serif;
    font-size: 0.82rem;
    font-weight: 500;
    cursor: pointer;
    transition: all 0.2s;
  }
  .tab-btn:hover { border-color: var(--gold); color: var(--gold); }
  .tab-btn.active {
    background: var(--gold);
    color: #000;
    border-color: var(--gold);
    font-weight: 600;
  }

  /* MAIN */
  main { max-width: 960px; margin: 0 auto; padding: 2rem 1.5rem 4rem; }

  /* SECTION PANELS */
  .panel { display: none; }
  .panel.active { display: block; }

  /* UNIT HEADER */
  .unit-header {
    display: flex;
    align-items: center;
    gap: 1rem;
    margin: 2rem 0 1rem;
  }
  .unit-num {
    font-family: 'JetBrains Mono', monospace;
    background: var(--gold);
    color: #000;
    width: 36px; height: 36px;
    border-radius: 8px;
    display: flex; align-items: center; justify-content: center;
    font-size: 0.85rem; font-weight: 700; flex-shrink: 0;
  }
  .unit-title {
    font-family: 'Playfair Display', serif;
    font-size: 1.15rem;
    color: #fff;
  }

  /* ACCORDION */
  .accordion {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    margin-bottom: 0.75rem;
    overflow: hidden;
    transition: border-color 0.2s;
  }
  .accordion:hover { border-color: rgba(240,180,41,0.45); }
  .acc-header {
    display: flex;
    align-items: flex-start;
    gap: 1rem;
    padding: 1rem 1.2rem;
    cursor: pointer;
    user-select: none;
  }
  .q-num {
    flex-shrink: 0;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.78rem;
    color: var(--gold);
    background: rgba(240,180,41,0.1);
    border: 1px solid rgba(240,180,41,0.25);
    padding: 0.2rem 0.55rem;
    border-radius: 5px;
    margin-top: 2px;
  }
  .q-text {
    flex: 1;
    font-size: 0.92rem;
    font-weight: 500;
    color: var(--text);
    line-height: 1.5;
  }
  .acc-arrow {
    flex-shrink: 0;
    width: 24px; height: 24px;
    border-radius: 50%;
    border: 1px solid rgba(255,255,255,0.15);
    display: flex; align-items: center; justify-content: center;
    color: var(--muted);
    font-size: 0.7rem;
    transition: all 0.25s;
    margin-top: 2px;
  }
  .accordion.open .acc-arrow {
    background: var(--gold);
    color: #000;
    border-color: var(--gold);
    transform: rotate(180deg);
  }
  .acc-body {
    display: none;
    padding: 0 1.2rem 1.2rem 1.2rem;
    border-top: 1px solid rgba(255,255,255,0.06);
  }
  .accordion.open .acc-body { display: block; }

  /* ANSWER STYLES */
  .marks-tag {
    display: inline-block;
    background: rgba(59,130,246,0.12);
    border: 1px solid rgba(59,130,246,0.3);
    color: #93c5fd;
    font-size: 0.72rem;
    font-weight: 600;
    padding: 0.15rem 0.6rem;
    border-radius: 4px;
    margin: 0.75rem 0 0.5rem;
    letter-spacing: 0.5px;
  }
  .ans-block { margin-top: 0.6rem; }
  .ans-label {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    font-size: 0.78rem;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 1px;
    color: var(--gold);
    margin: 0.9rem 0 0.35rem;
  }
  .ans-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: rgba(240,180,41,0.2);
  }
  .ans-text {
    font-size: 0.88rem;
    color: #cbd5e1;
    line-height: 1.75;
  }
  .ans-text b { color: var(--gold2); font-weight: 600; }
  .ans-text em { color: var(--purple); font-style: normal; font-weight: 500; }
  ul.ans-list {
    list-style: none;
    margin: 0.4rem 0;
    padding-left: 0;
  }
  ul.ans-list li {
    padding: 0.25rem 0 0.25rem 1.4rem;
    position: relative;
    font-size: 0.87rem;
    color: #cbd5e1;
    line-height: 1.65;
  }
  ul.ans-list li::before {
    content: '▸';
    position: absolute;
    left: 0;
    color: var(--gold);
    font-size: 0.75rem;
    top: 0.35rem;
  }
  ul.ans-list li b { color: var(--gold2); }

  .highlight-box {
    background: rgba(240,180,41,0.07);
    border-left: 3px solid var(--gold);
    border-radius: 0 8px 8px 0;
    padding: 0.7rem 1rem;
    margin: 0.6rem 0;
    font-size: 0.87rem;
    color: #e2e8f0;
    line-height: 1.65;
  }
  .highlight-box b { color: var(--gold2); }

  .formula-box {
    background: rgba(16,185,129,0.07);
    border: 1px solid rgba(16,185,129,0.25);
    border-radius: 8px;
    padding: 0.7rem 1rem;
    margin: 0.5rem 0;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.82rem;
    color: #6ee7b7;
    line-height: 1.6;
  }

  /* SHORT ANS */
  .short-ans {
    background: rgba(255,255,255,0.02);
    border-radius: 8px;
    padding: 0.8rem 1rem;
    font-size: 0.87rem;
    color: #cbd5e1;
    line-height: 1.7;
    margin-top: 0.6rem;
  }
  .short-ans b { color: var(--gold2); }

  /* SECTION INTRO */
  .section-intro {
    background: rgba(240,180,41,0.06);
    border: 1px solid rgba(240,180,41,0.2);
    border-radius: var(--radius);
    padding: 1rem 1.3rem;
    margin-bottom: 1.5rem;
    font-size: 0.85rem;
    color: var(--muted);
  }
  .section-intro strong { color: var(--gold); }

  /* DIVIDER */
  .unit-divider {
    height: 1px;
    background: linear-gradient(to right, transparent, rgba(240,180,41,0.3), transparent);
    margin: 2rem 0 1rem;
  }

  /* FOOTER */
  footer {
    text-align: center;
    padding: 2rem;
    color: var(--muted);
    font-size: 0.8rem;
    border-top: 1px solid rgba(255,255,255,0.06);
  }
  footer span { color: var(--gold); }

  @media (max-width: 600px) {
    main { padding: 1rem 1rem 3rem; }
    .acc-header { padding: 0.85rem 1rem; gap: 0.7rem; }
    .q-text { font-size: 0.86rem; }
  }
</style>
</head>
<body>

<header>
  <div class="badge">📘 B.Com Semester VI • OSOU</div>
  <h1>Fundamentals of <span>Corporate Tax Planning</span></h1>
  <p>DSE-III — Exam-Ready Study Material | Probable Questions & Model Answers</p>

</header>

<nav class="tab-bar">
  <button class="tab-btn active" onclick="switchTab('long')">📝 Long Questions</button>
  <button class="tab-btn" onclick="switchTab('short')">✏️ Short Questions</button>
</nav>

<main>

<!-- ==================== LONG QUESTIONS ==================== -->
<div id="panel-long" class="panel active">

  <div class="section-intro">
    <strong>📌 Long Questions (7 Marks each)</strong> — Write 250–350 words. Include Definition → Explanation → Key Points → Example → Conclusion. All questions below are high-probability exam questions.
  </div>

  <!-- UNIT 1 -->
  <div class="unit-header">
    <div class="unit-num">1</div>
    <div class="unit-title">Unit 1 — Introduction to Tax Planning &amp; Residential Status</div>
  </div>

  <!-- LQ1 -->
  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">L1.1</span>
      <span class="q-text">What is tax planning? What are the pre-requisites and limitations of tax planning?</span>
      <span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="marks-tag">⭐ 7 Marks | ~300 words</div>
      <div class="ans-block">
        <div class="ans-label">🔹 Definition</div>
        <div class="ans-text"><b>Tax planning</b> is the process of arranging one's financial affairs in such a way as to <b>minimize tax liability legally</b> by taking full advantage of all permissible deductions, exemptions, rebates, and reliefs under the Income Tax Act.</div>

        <div class="ans-label">🔹 Pre-requisites of Tax Planning</div>
        <ul class="ans-list">
          <li><b>Knowledge of Tax Laws:</b> A thorough understanding of the Income Tax Act, rules, and amendments is essential.</li>
          <li><b>Proper Maintenance of Accounts:</b> Accurate and updated books of accounts are required to plan taxes effectively.</li>
          <li><b>Understanding Income Sources:</b> All sources of income — business, salary, capital gains, etc. — must be known in advance.</li>
          <li><b>Long-term Financial Planning:</b> Tax planning should be integrated with the overall financial plan of the business.</li>
          <li><b>Knowledge of Deductions &amp; Exemptions:</b> Awareness of Sections 80C, 80D, 10, etc., helps in effective planning.</li>
          <li><b>Professional Guidance:</b> Assistance of a chartered accountant or tax consultant is necessary for complex matters.</li>
        </ul>

        <div class="ans-label">🔹 Limitations of Tax Planning</div>
        <ul class="ans-list">
          <li><b>Frequent Changes in Law:</b> Amendments in the Finance Act every year make planning uncertain and short-lived.</li>
          <li><b>Complexity of Tax Provisions:</b> The Income Tax Act is vast and complex, making it difficult for a layman.</li>
          <li><b>Anti-avoidance Provisions:</b> GAAR (General Anti-Avoidance Rules) restrict certain aggressive tax planning strategies.</li>
          <li><b>Uncertainty of Court Decisions:</b> Judicial interpretations keep changing, making planning outcomes uncertain.</li>
          <li><b>Limited to Legal Means Only:</b> Tax planning cannot cross the line into tax evasion.</li>
          <li><b>Short-term Focus:</b> Sometimes planning reduces current tax but increases future liability.</li>
        </ul>

        <div class="highlight-box"><b>Conclusion:</b> Tax planning is an important and legal tool for minimizing tax burden. However, it requires in-depth knowledge, professional guidance, and awareness of its limitations to be truly effective.</div>
      </div>
    </div>
  </div>

  <!-- LQ2 -->
  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">L1.2</span>
      <span class="q-text">Define tax and tax planning. Describe the features and objectives of tax planning.</span>
      <span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="marks-tag">⭐ 7 Marks | ~300 words</div>
      <div class="ans-block">
        <div class="ans-label">🔹 Definition of Tax</div>
        <div class="ans-text"><b>Tax</b> is a compulsory monetary contribution levied by the government on individuals and businesses to fund public expenditures. It is not a payment for a specific service, and non-payment attracts penalties.</div>

        <div class="ans-label">🔹 Definition of Tax Planning</div>
        <div class="ans-text"><b>Tax Planning</b> means the arrangement of financial transactions in a manner that reduces tax liability to the minimum permissible level by using legitimate provisions of the tax law.</div>

        <div class="ans-label">🔹 Features of Tax Planning</div>
        <ul class="ans-list">
          <li><b>Legal in Nature:</b> It uses only lawful means provided under the Income Tax Act.</li>
          <li><b>Reduces Tax Burden:</b> The primary aim is to reduce tax liability within legal limits.</li>
          <li><b>Advance in Nature:</b> Tax planning is done before the tax liability arises.</li>
          <li><b>Based on Existing Provisions:</b> It relies on deductions, exemptions, and reliefs in the Act.</li>
          <li><b>Productive Investment:</b> It encourages channeling savings into tax-saving instruments.</li>
          <li><b>Long-term Perspective:</b> Effective planning considers long-term financial and tax impact.</li>
        </ul>

        <div class="ans-label">🔹 Objectives of Tax Planning</div>
        <ul class="ans-list">
          <li><b>Minimization of Tax Liability:</b> To reduce taxes paid legally.</li>
          <li><b>Productive Use of Savings:</b> Savings from taxes are redirected into investments.</li>
          <li><b>Economic Growth:</b> Encourages investment in priority sectors (e.g., infrastructure, R&amp;D).</li>
          <li><b>Healthy Cash Flow:</b> Proper planning ensures adequate liquidity for the business.</li>
          <li><b>Compliance with Laws:</b> Ensures all obligations are met without penalties.</li>
          <li><b>Avoidance of Litigation:</b> Well-planned taxes reduce disputes with tax authorities.</li>
        </ul>

        <div class="highlight-box"><b>Conclusion:</b> Tax planning is a legitimate and essential business strategy. Its features make it distinct from tax evasion, and its objectives align with both business interests and national economic goals.</div>
      </div>
    </div>
  </div>

  <!-- LQ3 -->
  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">L1.3</span>
      <span class="q-text">What is residential status? Explain the provisions of corporate residential status and its incidence of tax.</span>
      <span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="marks-tag">⭐ 7 Marks | ~300 words</div>
      <div class="ans-block">
        <div class="ans-label">🔹 Meaning of Residential Status</div>
        <div class="ans-text"><b>Residential status</b> determines the scope of income chargeable to tax in India. It is determined every year for the <b>previous year</b> and decides whether an assessee is taxed on global income or only Indian income.</div>

        <div class="ans-label">🔹 Residential Status of a Company (Section 6(3))</div>
        <div class="ans-text">A company is classified as <b>Resident</b> or <b>Non-Resident</b> in India:</div>
        <ul class="ans-list">
          <li><b>Indian Company:</b> Always treated as <em>Resident in India</em>, regardless of where it is managed.</li>
          <li><b>Foreign Company:</b> Treated as Resident if its <b>Place of Effective Management (POEM)</b> is in India during the previous year.</li>
          <li><b>Non-Resident Company:</b> A foreign company whose POEM is NOT in India.</li>
        </ul>

        <div class="highlight-box"><b>POEM (Place of Effective Management)</b> refers to the place where key management and commercial decisions necessary for the conduct of business are made in substance.</div>

        <div class="ans-label">🔹 Incidence of Tax</div>
        <ul class="ans-list">
          <li><b>Resident Company:</b> Taxable on <b>worldwide income</b> — income received or accrued anywhere in the world is included.</li>
          <li><b>Non-Resident Company:</b> Taxable only on income <b>received or accrued in India</b>.</li>
        </ul>

        <div class="ans-label">🔹 Tax Rates</div>
        <ul class="ans-list">
          <li>Domestic Companies: <b>22%</b> (under Section 115BAA) + surcharge + cess</li>
          <li>New Manufacturing Companies: <b>15%</b> (under Section 115BAB)</li>
          <li>Foreign Companies: <b>40%</b> on Indian income</li>
        </ul>

        <div class="highlight-box"><b>Conclusion:</b> Residential status is a critical concept in corporate taxation. It determines how much of a company's income is subject to Indian tax, and companies must carefully assess their POEM to determine their tax obligations.</div>
      </div>
    </div>
  </div>

  <!-- LQ4 -->
  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">L1.4</span>
      <span class="q-text">What is tax planning? What are the implications of tax planning?</span>
      <span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="marks-tag">⭐ 7 Marks | ~280 words</div>
      <div class="ans-block">
        <div class="ans-label">🔹 Definition</div>
        <div class="ans-text"><b>Tax planning</b> is the arrangement of financial affairs in a manner that minimizes tax liability by legally availing deductions, exemptions, and reliefs under tax law. It is forward-looking and relies on provisions of the Income Tax Act.</div>

        <div class="ans-label">🔹 Implications of Tax Planning</div>
        <div class="ans-text">The implications refer to the <b>effects and consequences</b> of tax planning decisions on the business:</div>
        <ul class="ans-list">
          <li><b>Choice of Business Structure:</b> A company may choose between a proprietorship, partnership, or company form to minimize tax liability.</li>
          <li><b>Timing of Income &amp; Expenses:</b> Deferring income or accelerating deductions to a later or earlier year to reduce current year tax.</li>
          <li><b>Capital vs Revenue Expenditure:</b> Classifying expenses correctly impacts deductibility and tax liability.</li>
          <li><b>Investment Decisions:</b> Investing in tax-saving instruments (ELSS, PPF, etc.) under Section 80C reduces taxable income.</li>
          <li><b>Dividend Policy:</b> Planning dividend distribution to manage tax liability efficiently under DDT provisions.</li>
          <li><b>Depreciation Policy:</b> Choosing the right depreciation method and rate affects taxable profit.</li>
          <li><b>Transfer Pricing:</b> In multinationals, inter-company transactions must be priced at arm's length to avoid disputes.</li>
          <li><b>Carry Forward of Losses:</b> Proper planning allows losses to be carried forward and set off in future years.</li>
        </ul>

        <div class="highlight-box"><b>Conclusion:</b> Tax planning has wide implications on financial decisions. It helps businesses legally minimize tax liability while ensuring compliance. Every major business decision has a tax implication that must be planned in advance.</div>
      </div>
    </div>
  </div>

  <div class="unit-divider"></div>

  <!-- UNIT 2 -->
  <div class="unit-header">
    <div class="unit-num">2</div>
    <div class="unit-title">Unit 2 — Set Off &amp; Carry Forward of Losses</div>
  </div>

  <!-- LQ5 -->
  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">L2.1</span>
      <span class="q-text">Briefly explain the provisions of set off and carry forward of losses.</span>
      <span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="marks-tag">⭐ 7 Marks | ~300 words</div>
      <div class="ans-block">
        <div class="ans-label">🔹 Meaning</div>
        <div class="ans-text">When a taxpayer incurs a <b>loss under any head of income</b>, the Income Tax Act allows such losses to be adjusted against income either in the <b>same year (Set Off)</b> or in <b>future years (Carry Forward)</b>.</div>

        <div class="ans-label">🔹 Set Off of Losses</div>
        <div class="ans-text">Set off means <b>adjusting a loss against income of the same year</b>. It is of two types:</div>
        <ul class="ans-list">
          <li><b>Intra-head Set Off (Sec 70):</b> Loss from one source can be set off against income from another source under the <em>same head</em>. <br>E.g., Loss from one business adjusted against profit from another business.</li>
          <li><b>Inter-head Set Off (Sec 71):</b> Loss under one head can be set off against income under another head.<br>E.g., Loss from house property can be set off against salary income.</li>
        </ul>

        <div class="ans-label">🔹 Carry Forward of Losses</div>
        <div class="ans-text">If the loss cannot be fully set off in the same year, the <b>remaining loss can be carried forward</b> to subsequent years:</div>
        <ul class="ans-list">
          <li><b>Business Loss (Sec 72):</b> Can be carried forward for <b>8 years</b>. Can be set off only against business income. Return must be filed on time.</li>
          <li><b>Capital Loss (Sec 74):</b> Short-term capital loss — CF for <b>8 years</b>, set off against any capital gain. Long-term capital loss — CF for <b>8 years</b>, set off only against LTCG.</li>
          <li><b>Loss from House Property (Sec 71B):</b> Carry forward for <b>8 years</b> against house property income only.</li>
          <li><b>Speculation Loss (Sec 73):</b> Carry forward for <b>4 years</b>, set off only against speculation profit.</li>
          <li><b>Unabsorbed Depreciation (Sec 32(2)):</b> Can be carried forward for <b>indefinite years</b>.</li>
        </ul>

        <div class="highlight-box"><b>Conclusion:</b> The provisions for set off and carry forward are a significant benefit to taxpayers, reducing the net tax burden and promoting business continuity even during loss-making periods.</div>
      </div>
    </div>
  </div>

  <!-- LQ6 -->
  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">L2.2</span>
      <span class="q-text">Discuss the provision of intra and inter source adjustment of loss under section 70 and 71.</span>
      <span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="marks-tag">⭐ 7 Marks | ~300 words</div>
      <div class="ans-block">
        <div class="ans-label">🔹 Introduction</div>
        <div class="ans-text">The Income Tax Act provides for adjustment of losses to reduce taxable income. Sections 70 and 71 deal with <b>intra-head</b> and <b>inter-head</b> adjustments respectively.</div>

        <div class="ans-label">🔹 Section 70 — Intra-Head (Intra-Source) Adjustment</div>
        <div class="ans-text"><b>Intra-head adjustment</b> means the loss from one source under a particular head of income is set off against income from another source under the <em>same head</em>.</div>
        <ul class="ans-list">
          <li>Loss from one business ↔ Profit from another business (same head: PGBP)</li>
          <li>Loss from one house property ↔ Income from another house property</li>
          <li>Loss from short-term capital asset ↔ Gain from another short-term capital asset</li>
        </ul>
        <div class="highlight-box"><b>Exceptions:</b> Losses from speculation business and long-term capital loss cannot be set off against any other source under Section 70.</div>

        <div class="ans-label">🔹 Section 71 — Inter-Head Adjustment</div>
        <div class="ans-text"><b>Inter-head adjustment</b> allows a loss under one head of income to be set off against income under a <b>different head</b> in the same year.</div>
        <ul class="ans-list">
          <li>Loss from House Property can be set off against Salary, PGBP, etc.</li>
          <li>Loss from PGBP can be set off against income from other heads.</li>
        </ul>
        <div class="highlight-box"><b>Exceptions to Section 71:</b>
          <br>▸ Speculation business loss cannot be set off under inter-head.
          <br>▸ Capital loss cannot be set off against income under any other head.
          <br>▸ Loss from owning and maintaining race horses cannot be inter-head adjusted.</div>

        <div class="ans-label">🔹 Order of Adjustment</div>
        <ul class="ans-list">
          <li><b>Step 1:</b> Intra-head set off (Sec 70)</li>
          <li><b>Step 2:</b> Inter-head set off (Sec 71)</li>
          <li><b>Step 3:</b> Carry forward remaining loss to next year</li>
        </ul>

        <div class="highlight-box"><b>Conclusion:</b> Sections 70 and 71 are taxpayer-friendly provisions that help reduce net tax liability by allowing losses to offset gains within permissible limits.</div>
      </div>
    </div>
  </div>

  <div class="unit-divider"></div>

  <!-- UNIT 3 -->
  <div class="unit-header">
    <div class="unit-num">3</div>
    <div class="unit-title">Unit 3 — Capital Gains &amp; Slump Sale</div>
  </div>

  <!-- LQ7 -->
  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">L3.1</span>
      <span class="q-text">What is slump sale? How do you calculate capital gain on slump sale?</span>
      <span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="marks-tag">⭐ 7 Marks | ~300 words</div>
      <div class="ans-block">
        <div class="ans-label">🔹 Definition of Slump Sale (Section 50B)</div>
        <div class="ans-text"><b>Slump sale</b> means the <b>transfer of one or more undertakings</b> as a result of sale for a <b>lump sum consideration</b>, without values being individually assigned to the assets and liabilities transferred.</div>

        <div class="ans-label">🔹 Key Features</div>
        <ul class="ans-list">
          <li>The entire undertaking is sold as a going concern.</li>
          <li>A single lump sum price is agreed upon — no individual pricing of assets.</li>
          <li>It is covered under <b>Section 50B</b> of the Income Tax Act.</li>
          <li>Capital gain from slump sale is always treated as <b>Long-term Capital Gain</b> if the undertaking is held for more than 36 months, otherwise it is Short-term.</li>
        </ul>

        <div class="ans-label">🔹 Calculation of Capital Gain on Slump Sale</div>
        <div class="formula-box">
Capital Gain = Full Value of Consideration (Sale Price)
              MINUS
              Net Worth of the Undertaking

Net Worth = Aggregate value of total assets − Aggregate value of total liabilities
(Assets valued at book value, not market value)
        </div>
        <ul class="ans-list">
          <li><b>No deduction</b> for cost of improvement or indexation is allowed.</li>
          <li>Depreciable assets are taken at <b>Written Down Value (WDV)</b>.</li>
          <li>Other assets at <b>book value</b>.</li>
        </ul>

        <div class="ans-label">🔹 Example</div>
        <div class="highlight-box">
          Sale consideration of undertaking = ₹50,00,000<br>
          Total assets (WDV/Book) = ₹40,00,000<br>
          Total liabilities = ₹15,00,000<br>
          <b>Net Worth = 40,00,000 − 15,00,000 = ₹25,00,000</b><br>
          <b>Capital Gain = 50,00,000 − 25,00,000 = ₹25,00,000</b>
        </div>

        <div class="highlight-box"><b>Conclusion:</b> Slump sale is a unique mode of business transfer where capital gain is computed based on Net Worth rather than individual asset values. It is governed by Section 50B and always classified as long-term or short-term based on holding period.</div>
      </div>
    </div>
  </div>

  <!-- LQ8 -->
  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">L3.2</span>
      <span class="q-text">Discuss the provisions of valuation and treatment of sale of scientific research assets.</span>
      <span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="marks-tag">⭐ 7 Marks | ~280 words</div>
      <div class="ans-block">
        <div class="ans-label">🔹 Introduction</div>
        <div class="ans-text">When assets used for <b>scientific research</b> are sold, the Income Tax Act contains special provisions under <b>Section 41(3)</b> regarding the taxation of gains.</div>

        <div class="ans-label">🔹 Key Provisions (Section 41(3))</div>
        <ul class="ans-list">
          <li>If an asset used for scientific research is sold, the <b>entire sale proceeds</b> (not just the profit) are treated as income.</li>
          <li>The income is assessed under the head <b>"Profits and Gains of Business or Profession"</b> — NOT under capital gains.</li>
          <li>The amount taxable = <b>Lower of (i) Sale proceeds or (ii) Original cost of asset</b>.</li>
          <li>If sale proceeds exceed original cost, the excess is treated as <b>Capital Gain</b> under Section 50.</li>
          <li>Since no depreciation is charged on research assets, the <b>WDV = Original Cost</b>.</li>
        </ul>

        <div class="ans-label">🔹 Valuation</div>
        <ul class="ans-list">
          <li>The asset is valued at <b>original cost</b> (as no depreciation is allowed during research use).</li>
          <li>On sale, cost of acquisition = Original cost for computing capital gain on excess amount.</li>
        </ul>

        <div class="ans-label">🔹 Example</div>
        <div class="highlight-box">
          Asset original cost = ₹10,00,000<br>
          Sale price = ₹14,00,000<br>
          <b>Taxable as Business Income (Sec 41(3)):</b> ₹10,00,000<br>
          <b>Taxable as Capital Gain (Excess):</b> ₹4,00,000
        </div>

        <div class="highlight-box"><b>Conclusion:</b> Section 41(3) ensures that tax benefits originally given for scientific research are recovered on sale. The provision balances the incentive for research with tax recovery upon disposal of assets.</div>
      </div>
    </div>
  </div>

  <!-- LQ9 -->
  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">L3.3</span>
      <span class="q-text">Capital Gain — Practical Problem (Model Numerical)</span>
      <span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="marks-tag">⭐ SURE NUMERICAL | Step-by-Step</div>
      <div class="ans-block">
        <div class="ans-label">🔹 Model Problem</div>
        <div class="highlight-box">
          Mr. Sharma sold a house property on 01/11/2023 for ₹80,00,000.<br>
          He had purchased it on 01/04/2015 for ₹20,00,000.<br>
          Cost of improvement in 2018-19 = ₹5,00,000.<br>
          Brokerage paid = ₹1,00,000.<br>
          <em>CII: 2015-16 = 254 | 2018-19 = 280 | 2023-24 = 348</em><br>
          Compute LTCG.
        </div>

        <div class="ans-label">🔹 Step-by-Step Solution</div>
        <div class="formula-box">
Step 1: Full Value of Consideration = ₹80,00,000

Step 2: Less — Expenses on Transfer (Brokerage) = ₹1,00,000
        Net Consideration = ₹79,00,000

Step 3: Indexed Cost of Acquisition
        = 20,00,000 × (348/254) = ₹27,40,157

Step 4: Indexed Cost of Improvement
        = 5,00,000 × (348/280) = ₹6,21,429

Step 5: Long Term Capital Gain (LTCG)
        = Net Consideration − (ICOA + ICOI)
        = 79,00,000 − (27,40,157 + 6,21,429)
        = 79,00,000 − 33,61,586
        = ₹45,38,414

Tax on LTCG = 20% + Surcharge + Cess (under Section 112)
        </div>

        <div class="highlight-box"><b>Key Formulas to Remember:</b><br>
        ▸ ICOA = Cost × (CII of year of sale / CII of year of purchase)<br>
        ▸ LTCG = Net Sale − ICOA − ICOI<br>
        ▸ Holding &gt; 24 months for immovable property → LTCA<br>
        ▸ Short-term: no indexation benefit</div>
      </div>
    </div>
  </div>

  <!-- LQ10 -->
  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">L3.4</span>
      <span class="q-text">Exemptions provisions of Capital Gain under Section 54.</span>
      <span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="marks-tag">⭐ 7 Marks | ~280 words</div>
      <div class="ans-block">
        <div class="ans-label">🔹 Introduction</div>
        <div class="ans-text">The Income Tax Act provides exemptions from capital gains to encourage <b>reinvestment</b> and housing. Section 54 is the most important exemption available to <b>individuals and HUFs</b> on sale of residential house property.</div>

        <div class="ans-label">🔹 Conditions for Section 54 Exemption</div>
        <ul class="ans-list">
          <li>The assessee must be an <b>Individual or HUF</b>.</li>
          <li>The asset transferred must be a <b>Long-Term Capital Asset</b> — a residential house property.</li>
          <li>The capital gain must be invested in <b>purchasing a new residential house</b>:
            <br>— Within <b>1 year before</b> or <b>2 years after</b> the sale, OR
            <br>— Within <b>3 years</b> if constructing a new house.</li>
          <li>Only <b>1 new residential house</b> can be purchased in India (from AY 2020-21, up to 2 houses if LTCG ≤ ₹2 crore — once in lifetime).</li>
        </ul>

        <div class="ans-label">🔹 Amount of Exemption</div>
        <div class="formula-box">
Exemption = Lower of:
(i)  Amount of LTCG
(ii) Cost of new house purchased/constructed
        </div>
        <div class="ans-text">If the new house is sold within <b>3 years</b> of purchase, the exemption is withdrawn and cost of new asset is reduced by the exempted LTCG.</div>

        <div class="ans-label">🔹 Capital Gain Account Scheme (CGAS)</div>
        <div class="ans-text">If the capital gain cannot be invested before the due date of filing return, it must be deposited in a <b>Capital Gain Account Scheme (CGAS)</b> with a scheduled bank and utilized within the specified period.</div>

        <div class="highlight-box"><b>Conclusion:</b> Section 54 is a major relief for individuals selling residential properties. It encourages reinvestment in housing and reduces the tax burden provided the conditions are strictly followed.</div>
      </div>
    </div>
  </div>

  <div class="unit-divider"></div>

  <!-- UNIT 4 -->
  <div class="unit-header">
    <div class="unit-num">4</div>
    <div class="unit-title">Unit 4 — Returns, Assessment, Double Taxation &amp; E-Filing</div>
  </div>

  <!-- LQ11 -->
  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">L4.1</span>
      <span class="q-text">What is e-filing? Explain the procedures of e-filing returns.</span>
      <span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="marks-tag">⭐ 7 Marks | ~280 words</div>
      <div class="ans-block">
        <div class="ans-label">🔹 Meaning of E-filing</div>
        <div class="ans-text"><b>E-filing</b> means filing the <b>Income Tax Return (ITR) electronically</b> through the official portal of the Income Tax Department: <b>www.incometax.gov.in</b>. It replaces the traditional paper-based filing process.</div>

        <div class="ans-label">🔹 Who Must Mandatorily E-file?</div>
        <ul class="ans-list">
          <li>All companies and firms required to get accounts audited.</li>
          <li>Individuals having income above ₹5 lakh.</li>
          <li>Persons claiming refund of tax.</li>
          <li>Persons with foreign assets or signing authority in foreign accounts.</li>
        </ul>

        <div class="ans-label">🔹 Step-by-Step Procedure of E-filing</div>
        <ul class="ans-list">
          <li><b>Step 1 — Registration:</b> Register on incometax.gov.in using PAN as User ID.</li>
          <li><b>Step 2 — Select Correct ITR Form:</b> Choose the appropriate ITR form (ITR-1 to ITR-7) based on income type.</li>
          <li><b>Step 3 — Download/Fill Form:</b> Fill in details like income, deductions, TDS, advance tax.</li>
          <li><b>Step 4 — Calculate Tax:</b> Compute total tax liability, including surcharge and cess.</li>
          <li><b>Step 5 — Pay Self-Assessment Tax:</b> If any tax is due, pay via Challan 280 online.</li>
          <li><b>Step 6 — Upload Return:</b> Submit the completed ITR form on the portal.</li>
          <li><b>Step 7 — Verification (e-Verify):</b> Verify using Aadhaar OTP, Net Banking, DSC, or send signed ITR-V to CPC Bengaluru within 30 days.</li>
          <li><b>Step 8 — Acknowledgement:</b> Receive ITR-V (acknowledgement) via registered email.</li>
        </ul>

        <div class="highlight-box"><b>Conclusion:</b> E-filing has simplified return submission, reduced errors, and expedited processing and refunds. It is mandatory for most taxpayers and promotes transparency in tax compliance.</div>
      </div>
    </div>
  </div>

  <!-- LQ12 -->
  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">L4.2</span>
      <span class="q-text">What do you mean by double taxation? What are the means and types of double taxation reliefs?</span>
      <span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="marks-tag">⭐ 7 Marks | ~300 words</div>
      <div class="ans-block">
        <div class="ans-label">🔹 Meaning of Double Taxation</div>
        <div class="ans-text"><b>Double taxation</b> occurs when the <b>same income is taxed twice</b> — either in two different countries or by two different taxing authorities. It is a major problem for international business and cross-border transactions.</div>

        <div class="ans-label">🔹 Types of Double Taxation</div>
        <ul class="ans-list">
          <li><b>Juridical Double Taxation:</b> When the <em>same person</em> is taxed on the <em>same income</em> in two different countries. (Most common type)</li>
          <li><b>Economic Double Taxation:</b> When the <em>same income</em> is taxed in the hands of <em>two different persons</em>. E.g., company pays tax on profits and then shareholder pays tax on dividend.</li>
        </ul>

        <div class="ans-label">🔹 Means of Double Taxation Relief</div>
        <ul class="ans-list">
          <li><b>Exemption Method:</b> Income is taxed in one country only; the other country exempts it fully.</li>
          <li><b>Tax Credit Method:</b> Tax paid in one country is given as credit against tax payable in the other country.</li>
          <li><b>Tax Deduction Method:</b> Tax paid abroad is allowed as a deduction from income.</li>
        </ul>

        <div class="ans-label">🔹 Types of Double Taxation Relief in India</div>
        <ul class="ans-list">
          <li><b>Unilateral Relief (Section 91):</b> India provides relief even when there is no agreement with the other country, if: (i) Assessee is resident in India, (ii) Income accrued outside India, (iii) Tax was paid in that country.</li>
          <li><b>Bilateral Relief — DTAA (Section 90):</b> India has entered into <b>Double Taxation Avoidance Agreements (DTAA)</b> with 90+ countries (UK, USA, etc.). Relief is provided through lower tax rates or exemptions on specific income.</li>
          <li><b>Specified Associations (Section 90A):</b> Agreements between specified associations of India and foreign countries.</li>
        </ul>

        <div class="highlight-box"><b>Conclusion:</b> Double taxation is a barrier to global investment. India's DTAA network and unilateral relief provisions under Sections 90 and 91 protect Indian residents from paying tax twice on the same income.</div>
      </div>
    </div>
  </div>

  <!-- LQ13 -->
  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">L4.3</span>
      <span class="q-text">What are circumstances of filling belated and revised return?</span>
      <span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="marks-tag">⭐ 7 Marks | ~270 words</div>
      <div class="ans-block">
        <div class="ans-label">🔹 Belated Return (Section 139(4))</div>
        <div class="ans-text">A <b>belated return</b> is filed when the assessee fails to file the original return by the <b>due date</b> specified under Section 139(1).</div>
        <ul class="ans-list">
          <li><b>Time Limit:</b> Can be filed up to <b>31st December</b> of the Assessment Year (after recent amendments).</li>
          <li><b>Consequences of Late Filing:</b>
            <br>▸ Interest under Section 234A
            <br>▸ Late fee under Section 234F: ₹5,000 (if income &gt; ₹5 lakh); ₹1,000 (if income ≤ ₹5 lakh)
            <br>▸ Cannot carry forward business losses (except unabsorbed depreciation)</li>
        </ul>
        <div class="highlight-box"><b>Circumstances for Belated Return:</b>
          <br>▸ Forgot to file within due date
          <br>▸ Awaiting documents or Form 16
          <br>▸ Tax audit not completed in time
          <br>▸ Technical issues on portal</div>

        <div class="ans-label">🔹 Revised Return (Section 139(5))</div>
        <div class="ans-text">A <b>revised return</b> is filed when the assessee <b>discovers any omission or wrong statement</b> in the original return that was filed in good faith.</div>
        <ul class="ans-list">
          <li><b>Time Limit:</b> Can be filed up to <b>31st December</b> of the Assessment Year or before completion of assessment, whichever is earlier.</li>
          <li>It <b>replaces</b> the original return completely.</li>
          <li>Can be revised <b>multiple times</b> within the time limit.</li>
        </ul>
        <div class="highlight-box"><b>Circumstances for Revised Return:</b>
          <br>▸ Wrong income figure entered
          <br>▸ Deduction under 80C/80D missed
          <br>▸ TDS entries not correctly reflected
          <br>▸ Bank account details were incorrect</div>

        <div class="highlight-box"><b>Conclusion:</b> Both belated and revised returns give taxpayers an opportunity to correct mistakes or late filing, though they come with potential interest and fee implications.</div>
      </div>
    </div>
  </div>

  <!-- LQ14 -->
  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">L4.4</span>
      <span class="q-text">What are different penalties for failure to submit business report within due date?</span>
      <span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="marks-tag">⭐ 7 Marks | ~260 words</div>
      <div class="ans-block">
        <div class="ans-label">🔹 Introduction</div>
        <div class="ans-text">The Income Tax Act imposes <b>penalties and interest</b> for failure to file returns, reports, and statements on time to ensure compliance and discourage defaults.</div>

        <div class="ans-label">🔹 Key Penalties</div>
        <ul class="ans-list">
          <li><b>Section 234F — Late Filing Fee:</b> ₹5,000 if return filed after due date (income &gt; ₹5 lakh); ₹1,000 if income ≤ ₹5 lakh.</li>
          <li><b>Section 234A — Interest for Late Filing:</b> 1% per month on unpaid tax from due date to actual filing date.</li>
          <li><b>Section 271B — Failure to Audit:</b> Penalty = 0.5% of turnover or ₹1,50,000 whichever is lower, for failure to get accounts audited under Section 44AB.</li>
          <li><b>Section 271BA — Failure to Submit Form 3CEB:</b> Penalty of ₹1,00,000 for failure to furnish transfer pricing report.</li>
          <li><b>Section 272A — Failure to Answer Questions / File Documents:</b> Penalty of ₹10,000 per default.</li>
          <li><b>Section 275 — General Penalty:</b> Up to ₹1,00,000 for various defaults where no specific penalty is prescribed.</li>
          <li><b>Section 276CC — Prosecution:</b> Willful failure to file return can lead to imprisonment of 3 months to 7 years depending on tax evaded.</li>
        </ul>

        <div class="highlight-box"><b>Conclusion:</b> The penalty structure under the Income Tax Act is designed to enforce timely compliance. Both monetary penalties and prosecution provisions ensure that businesses and individuals meet their filing obligations on time.</div>
      </div>
    </div>
  </div>

  <!-- LQ15 -->
  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">L4.5</span>
      <span class="q-text">What are the different types of assessment?</span>
      <span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="marks-tag">⭐ 7 Marks | ~300 words</div>
      <div class="ans-block">
        <div class="ans-label">🔹 Meaning of Assessment</div>
        <div class="ans-text"><b>Assessment</b> is the process by which the Income Tax Department determines the income and tax payable by a taxpayer. It is the official scrutiny and verification of the return filed.</div>

        <div class="ans-label">🔹 Types of Assessment</div>
        <ul class="ans-list">
          <li><b>1. Self-Assessment (Section 140A):</b> Done by the taxpayer himself before filing the return. The assessee computes his own income, tax liability, pays self-assessment tax, and files return.</li>
          <li><b>2. Summary Assessment / Intimation (Section 143(1)):</b> An automated computerized check performed by the IT department after return filing. Adjustments made for arithmetic errors, incorrect claims, etc. Intimation sent to taxpayer. No need to appear before AO.</li>
          <li><b>3. Scrutiny Assessment (Section 143(3)):</b> Detailed assessment by Assessing Officer (AO) when the return is selected for scrutiny. Taxpayer must furnish documents and explanations. AO can make additions or disallowances.</li>
          <li><b>4. Best Judgment Assessment (Section 144):</b> Done when taxpayer fails to file return, fails to comply with notices, or does not maintain proper accounts. AO estimates income to the best of his judgment.</li>
          <li><b>5. Income Escaping Assessment (Section 147/148):</b> When the AO has reason to believe that income has escaped assessment (not declared or underreported), a notice is issued and the case is reopened.</li>
          <li><b>6. Faceless Assessment:</b> Introduced in 2020. Assessment done electronically without physical interface between taxpayer and AO. All communication is online through the portal.</li>
        </ul>

        <div class="highlight-box"><b>Conclusion:</b> Different types of assessment serve different purposes — from self-reporting to government-initiated scrutiny. Understanding them helps taxpayers respond effectively to notices and comply with tax laws.</div>
      </div>
    </div>
  </div>

</div><!-- end panel-long -->


<!-- ==================== SHORT QUESTIONS ==================== -->
<div id="panel-short" class="panel">

  <div class="section-intro">
    <strong>📌 Short Questions (2–3 Marks each)</strong> — Write 2–4 lines (1–2 marks) or ~75 words (3 marks). Define → Explain briefly → Key point.
  </div>

  <!-- UNIT 1 SHORT -->
  <div class="unit-header">
    <div class="unit-num">1</div>
    <div class="unit-title">Unit 1 — Short Questions</div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S1.1</span><span class="q-text">What is tax?</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans"><b>Tax</b> is a compulsory financial charge levied by the government on individuals and organizations on their income, profits, or transactions. It is not a voluntary payment — failure to pay attracts penalties. Taxes are used to fund public services like roads, healthcare, and education. Major direct taxes include income tax and corporate tax.</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S1.2</span><span class="q-text">What is tax planning?</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans"><b>Tax planning</b> is the arrangement of financial affairs in a legal manner to minimize tax liability by availing all permissible deductions, exemptions, and reliefs under the Income Tax Act. It is lawful, proactive, and aimed at reducing tax burden without violating any provision of law.</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S1.3</span><span class="q-text">Explain tax management.</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans"><b>Tax management</b> refers to the process of <b>complying with tax laws</b> — timely filing of returns, payment of advance tax, TDS deductions, maintaining records, and avoiding penalties. While tax planning focuses on reducing liability, tax management focuses on fulfilling obligations efficiently. It is operational and day-to-day in nature.</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S1.4</span><span class="q-text">Explain tax avoidance.</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans"><b>Tax avoidance</b> means reducing tax liability by taking advantage of <b>loopholes</b> in the tax law. It is technically legal but against the spirit of the law. It involves structuring transactions in ways not intended by the legislature. GAAR (General Anti-Avoidance Rules) was introduced to curb aggressive tax avoidance in India.</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S1.5</span><span class="q-text">What do you mean by tax evasion?</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans"><b>Tax evasion</b> is the <b>illegal</b> act of deliberately hiding income, inflating expenses, or suppressing facts to reduce tax liability. It is a criminal offence under the Income Tax Act and can result in heavy penalties, prosecution, and imprisonment. Examples: maintaining two sets of accounts, not declaring cash income.</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S1.6</span><span class="q-text">Difference between tax avoidance and tax evasion.</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans">
        <b>Tax Avoidance vs Tax Evasion:</b><br><br>
        <b>Tax Avoidance:</b> Legal | Uses loopholes in law | Against spirit of law | Penalized through GAAR | No criminal liability<br><br>
        <b>Tax Evasion:</b> Illegal | Concealment of income | Direct violation of law | Criminal offence | Prosecution and imprisonment possible
      </div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S1.7</span><span class="q-text">What is Assessment Year and Financial Year?</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans"><b>Financial Year (FY) / Previous Year:</b> The year in which income is earned. It runs from <b>1st April to 31st March</b>. Example: FY 2023-24 = income earned from 1 April 2023 to 31 March 2024.<br><br><b>Assessment Year (AY):</b> The year <b>immediately following</b> the financial year in which income is assessed and taxed. Example: AY 2024-25 corresponds to income earned in FY 2023-24.</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S1.8</span><span class="q-text">Explain MAT (Minimum Alternate Tax).</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans"><b>MAT (Minimum Alternate Tax)</b> under <b>Section 115JB</b> ensures that companies with substantial book profits but zero or low taxable income (due to deductions) still pay a minimum tax. MAT is levied at <b>15%</b> of book profit + surcharge + cess. The excess MAT paid over normal tax can be carried forward as <b>MAT Credit</b> for 15 years.</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S1.9</span><span class="q-text">Types of companies.</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans">
        <b>Types of Companies for Tax Purposes:</b><br><br>
        ▸ <b>Domestic Company:</b> Indian company or foreign company with POEM in India<br>
        ▸ <b>Foreign Company:</b> Company not registered in India; POEM outside India<br>
        ▸ <b>Public Company:</b> Listed on stock exchange<br>
        ▸ <b>Private Company:</b> Not publicly traded<br>
        ▸ <b>Widely Held / Closely Held:</b> Based on public shareholding percentage
      </div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S1.10</span><span class="q-text">What is residential status?</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans"><b>Residential status</b> is a concept under the Income Tax Act that determines the <b>scope of taxable income</b> of a person. It is determined for each previous year. Based on residential status, the person is taxed on global income (resident) or only on India-sourced income (non-resident).</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S1.11</span><span class="q-text">Who is resident?</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans">A <b>company</b> is a <b>resident</b> in India if: (i) It is an <b>Indian company</b> (incorporated under Indian law), OR (ii) It is a foreign company whose <b>POEM (Place of Effective Management)</b> is in India during the previous year. Resident companies are taxed on their <b>worldwide income</b>.</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S1.12</span><span class="q-text">Tax avoidance vs Tax planning.</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans">
        <b>Tax Planning:</b> Reducing tax through legitimate provisions of the law; within the intent of the legislature; fully accepted and encouraged.<br><br>
        <b>Tax Avoidance:</b> Reducing tax by exploiting loopholes; technically legal but against the spirit of the law; curbed by GAAR provisions.
      </div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S1.13</span><span class="q-text">Different types of assessee.</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans">
        <b>Assessee</b> means a person liable to pay tax or file a return under the Income Tax Act. Types:<br><br>
        ▸ <b>Normal Assessee:</b> One who is liable to pay tax on own income<br>
        ▸ <b>Representative Assessee:</b> One who is liable on behalf of another person (e.g., guardian of minor)<br>
        ▸ <b>Deemed Assessee:</b> One who is treated as assessee by law (e.g., legal heir of deceased)<br>
        ▸ <b>Assessee in Default:</b> One who fails to meet tax obligations (e.g., employer failing to deduct TDS)
      </div>
    </div>
  </div>

  <div class="unit-divider"></div>

  <!-- UNIT 2 SHORT -->
  <div class="unit-header">
    <div class="unit-num">2</div>
    <div class="unit-title">Unit 2 — Short Questions</div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S2.1</span><span class="q-text">What is set off of losses?</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans"><b>Set off of losses</b> means adjusting a loss incurred under one head or source against income from another head or source in the <b>same assessment year</b>. It reduces the net taxable income for that year. Set off can be intra-head (Sec 70) or inter-head (Sec 71).</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S2.2</span><span class="q-text">What is carry forward of losses?</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans"><b>Carry forward of losses</b> means that a loss which cannot be fully set off in the current year is carried forward to <b>subsequent assessment years</b> for set off against future income. The period for carry forward varies — 8 years for business losses, indefinite for unabsorbed depreciation.</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S2.3</span><span class="q-text">What are intra-head adjustment of losses?</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans"><b>Intra-head adjustment (Section 70)</b> means setting off a loss from one source under a head of income against income from <b>another source under the same head</b>. Example: Loss from Business A can be set off against Profit from Business B (both under PGBP head). Exceptions: speculation loss, long-term capital loss.</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S2.4</span><span class="q-text">What are inter-head adjustment of losses?</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans"><b>Inter-head adjustment (Section 71)</b> allows a loss under one head of income to be set off against income under a <b>different head</b> in the same year. Example: Loss from house property set off against salary income. Exceptions: Capital loss and speculation loss cannot be inter-head adjusted.</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S2.5</span><span class="q-text">Provisions of set off and carry forward of loss from Capital Gain.</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans">
        ▸ <b>Short-term capital loss (STCL)</b> can be set off against both short-term and long-term capital gains.<br>
        ▸ <b>Long-term capital loss (LTCL)</b> can be set off only against long-term capital gains.<br>
        ▸ Capital losses CANNOT be set off against income under any other head.<br>
        ▸ Both STCL and LTCL can be carried forward for <b>8 assessment years</b>.<br>
        ▸ Return must be filed on time to carry forward capital losses.
      </div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S2.6</span><span class="q-text">Provisions of set off and carry forward of loss from Casual Income.</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans"><b>Casual income</b> (lottery, game shows, horse races) is taxed at a flat rate of <b>30%</b> under Section 115BB with no deductions. Loss from casual income <b>cannot be set off</b> against any other income, nor can it be carried forward. The law does not permit any set-off or carry forward for such losses as they are considered windfall gains.</div>
    </div>
  </div>

  <div class="unit-divider"></div>

  <!-- UNIT 3 SHORT -->
  <div class="unit-header">
    <div class="unit-num">3</div>
    <div class="unit-title">Unit 3 — Short Questions</div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S3.1</span><span class="q-text">Discuss the tax liability of capital gain in case of buy back of shares.</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans">When a company <b>buys back its own shares</b>, it is taxed under <b>Section 115QA</b>. The company pays <b>Buyback Tax @ 20%</b> on the distributed income (i.e., buyback consideration minus amount received by company at time of original issue). This tax is paid by the <b>company</b>, not the shareholder. The shareholder is <b>exempt</b> from capital gains tax on such buyback under Section 10(34A).</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S3.2</span><span class="q-text">What is capital asset?</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans"><b>Capital asset</b> under Section 2(14) means any property held by an assessee — land, building, shares, bonds, machinery, jewellery, etc. <b>Exceptions (NOT capital assets):</b> Stock-in-trade, personal movable property (clothes, furniture), agricultural land in rural India, Gold Bonds, and Special Bearer Bonds. Capital assets can be short-term or long-term based on holding period.</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S3.3</span><span class="q-text">What is un-absorbed depreciation?</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans"><b>Unabsorbed depreciation</b> is the depreciation that could not be fully set off against business income in the current year due to insufficient profit or loss. Under Section 32(2), it can be carried forward for an <b>indefinite number of years</b> (no time limit). It can be set off against <b>any head of income</b> (not just business income), which makes it more flexible than business losses.</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S3.4</span><span class="q-text">What do you mean by capital gain?</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans"><b>Capital gain</b> under Section 45 is the profit or gain arising from the <b>transfer of a capital asset</b> during a previous year. It is chargeable under the head "Capital Gains." Capital gain = Sale consideration − Cost of acquisition − Cost of improvement − Transfer expenses. Capital gains can be short-term or long-term based on the holding period of the asset.</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S3.5</span><span class="q-text">Explain about book profit.</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans"><b>Book profit</b> under Section 115JB is the net profit shown in the <b>Profit &amp; Loss account</b> prepared as per the Companies Act, after making certain specified adjustments (additions and deductions). It is the basis for calculating <b>MAT (Minimum Alternate Tax)</b>. MAT = 15% of book profit + surcharge + cess.</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S3.6</span><span class="q-text">State the purpose of accumulated losses.</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans"><b>Accumulated losses</b> refer to unabsorbed losses and depreciation of an amalgamating company. In <b>tax planning for mergers and amalgamations</b>, the acquiring company can set off these accumulated losses of the target company under Section 72A. Purpose: to reduce the tax liability of the combined entity and make the merger financially attractive.</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S3.7</span><span class="q-text">What is block of assets?</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans"><b>Block of assets</b> under Section 2(11) is a group of assets belonging to the <b>same class</b> (e.g., all buildings, or all machinery) and chargeable to depreciation at the same rate. Depreciation is calculated on the total WDV of the block, not individually for each asset. When all assets of a block are sold and sale proceeds exceed WDV, the excess is a short-term capital gain (Section 50).</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S3.8</span><span class="q-text">Written down value method of depreciation.</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans"><b>WDV (Written Down Value) method</b> calculates depreciation on the <b>reduced book value</b> of the asset each year, not on original cost. The WDV decreases each year as depreciation is deducted. It is the method prescribed under the <b>Income Tax Act (Section 32)</b> for tax purposes. Higher depreciation in early years; the asset never reaches zero value under this method.</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S3.9</span><span class="q-text">Short-term and Long-term Capital Assets.</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans">
        <b>Short-term Capital Asset (STCA):</b> Held for 36 months or less (24 months for immovable property; 12 months for listed shares/securities). Gains taxed at applicable slab rate or 15% (Sec 111A for listed shares).<br><br>
        <b>Long-term Capital Asset (LTCA):</b> Held for more than the above periods. Gains taxed at 20% with indexation (Sec 112) or 10% without indexation (Sec 112A for listed equity).
      </div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S3.10</span><span class="q-text">What is slump sale?</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans"><b>Slump sale (Section 50B)</b> means the transfer of one or more undertakings as a result of sale for a <b>lump sum consideration</b> without assigning individual values to assets and liabilities. Capital gain = Sale price − Net worth of undertaking. Long-term or short-term based on 36-month holding of undertaking.</div>
    </div>
  </div>

  <div class="unit-divider"></div>

  <!-- UNIT 4 SHORT -->
  <div class="unit-header">
    <div class="unit-num">4</div>
    <div class="unit-title">Unit 4 — Short Questions</div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S4.1</span><span class="q-text">Explain e-filing of return.</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans"><b>E-filing</b> is the electronic submission of income tax returns through <b>www.incometax.gov.in</b>. It is mandatory for companies, firms needing audit, and individuals with income above ₹5 lakh. Process: Register → Select ITR form → Fill details → Pay tax if due → Upload → e-Verify. Acknowledgement (ITR-V) is received via email.</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S4.2</span><span class="q-text">What is belated return?</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans">A <b>belated return (Section 139(4))</b> is filed after the due date but before <b>31st December</b> of the Assessment Year. Consequences include: interest under Section 234A, late fee under Section 234F (₹5,000 or ₹1,000), and inability to carry forward most losses. It gives taxpayers a second chance to comply.</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S4.3</span><span class="q-text">What are PAN, TIN?</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans">
        <b>PAN (Permanent Account Number):</b> A 10-character alphanumeric code issued by the Income Tax Department to every taxpayer. It is mandatory for filing returns, opening bank accounts, and transactions above specified limits. Example: ABCDE1234F.<br><br>
        <b>TIN (Tax Identification Number):</b> A unique number assigned to dealers registered under VAT/GST for tracking commercial transactions and tax payments.
      </div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S4.4</span><span class="q-text">What are TDS, TCS?</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans">
        <b>TDS (Tax Deducted at Source):</b> Tax deducted by the payer at the time of making payment (salary, rent, interest, etc.) and deposited with the government. It ensures regular tax collection throughout the year. Governed by Sections 192–194.<br><br>
        <b>TCS (Tax Collected at Source):</b> Tax collected by the seller from the buyer at the time of sale of specified goods (timber, scrap, minerals, etc.) under Section 206C.
      </div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S4.5</span><span class="q-text">Who are the persons compulsorily required to file return?</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans">
        Under Section 139(1), the following must mandatorily file return:<br>
        ▸ <b>Companies and Firms</b> — always<br>
        ▸ <b>Individuals/HUF/AOP</b> — if income exceeds basic exemption limit<br>
        ▸ Persons with foreign assets or foreign accounts<br>
        ▸ Persons depositing ₹1 crore+ in bank accounts<br>
        ▸ Persons spending ₹2 lakh+ on foreign travel<br>
        ▸ Persons paying ₹1 lakh+ electricity bills<br>
        ▸ Persons claiming refund of tax
      </div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S4.6</span><span class="q-text">What is double taxation?</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans"><b>Double taxation</b> refers to the situation where the <b>same income is taxed twice</b> — either in two countries (juridical double taxation) or in the hands of two different persons (economic double taxation). India prevents this through <b>DTAA (Double Taxation Avoidance Agreements)</b> under Section 90 with 90+ countries and unilateral relief under Section 91.</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S4.7</span><span class="q-text">Explain penalties and offences.</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans">
        Key penalties under the Income Tax Act:<br>
        ▸ <b>Sec 234F:</b> ₹5,000 late filing fee (₹1,000 if income ≤ ₹5L)<br>
        ▸ <b>Sec 271B:</b> Penalty for non-audit: 0.5% of turnover or ₹1.5L<br>
        ▸ <b>Sec 270A:</b> Underreporting income: 50% of tax on under-reported income; 200% for misreporting<br>
        ▸ <b>Sec 276CC:</b> Willful failure to file return → imprisonment 3 months to 7 years
      </div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S4.8</span><span class="q-text">What are casual incomes?</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans"><b>Casual incomes</b> are non-recurring, windfall incomes that cannot be regularly expected. Examples: lottery winnings, prize from game shows (KBC), crossword puzzles, horse race winnings. Taxable under <b>Section 115BB at flat 30%</b> (+ surcharge + cess), regardless of slab. No deductions or set-off of losses allowed against casual income.</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S4.9</span><span class="q-text">What is faceless assessment?</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans"><b>Faceless assessment</b> was introduced in 2020 under Section 143(3A). All scrutiny assessments are conducted <b>electronically without physical interaction</b> between taxpayer and Assessing Officer. Cases are randomly allocated across different units. It eliminates corruption and harassment. All communications are through the <b>e-proceeding portal</b> only.</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S4.10</span><span class="q-text">What is scrutiny assessment?</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans"><b>Scrutiny assessment (Section 143(3))</b> is a detailed examination of a tax return by the Assessing Officer (AO) when the return is selected for scrutiny. The AO issues a notice requiring the taxpayer to produce documents and evidence. After examination, the AO passes an assessment order, which may include additions or disallowances if the AO is not satisfied.</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S4.11</span><span class="q-text">Mode of filing return of income.</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans">
        Modes of filing ITR:<br>
        ▸ <b>Paper/Manual:</b> Physical forms submitted to IT office (allowed only for super senior citizens and specific cases)<br>
        ▸ <b>E-filing without DSC:</b> Upload ITR and verify via Aadhaar OTP/Net banking; then send ITR-V to CPC Bengaluru<br>
        ▸ <b>E-filing with DSC (Digital Signature Certificate):</b> ITR digitally signed; no physical verification needed<br>
        ▸ <b>Online Utility:</b> Direct online filing on incometax.gov.in
      </div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S4.12</span><span class="q-text">Who is assessee in default?</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans"><b>Assessee in default</b> is a person who fails to comply with the provisions of the Income Tax Act — for example, an employer who fails to deduct TDS on salary, or a deductor who deducts TDS but does not deposit it with the government. Such an assessee is liable for interest under Section 201(1A) and penalty.</div>
    </div>
  </div>

  <div class="accordion">
    <div class="acc-header" onclick="toggle(this)">
      <span class="q-num">S4.13</span><span class="q-text">Different types of assessment.</span><span class="acc-arrow">▼</span>
    </div>
    <div class="acc-body">
      <div class="short-ans">
        Types of assessment under the Income Tax Act:<br>
        ▸ <b>Self-Assessment (Sec 140A)</b> — by taxpayer himself<br>
        ▸ <b>Summary/Intimation (Sec 143(1))</b> — computerized check<br>
        ▸ <b>Scrutiny Assessment (Sec 143(3))</b> — detailed AO examination<br>
        ▸ <b>Best Judgment Assessment (Sec 144)</b> — AO estimates when taxpayer defaults<br>
        ▸ <b>Income Escaping Assessment (Sec 147)</b> — when income is not assessed<br>
        ▸ <b>Faceless Assessment</b> — electronic, no physical contact
      </div>
    </div>
  </div>

</div><!-- end panel-short -->

</main>

<footer>
  <p>📘 B.Com Sem VI | DSE-III — Fundamentals of <span>Corporate Tax Planning</span> | OSOU</p>
  <p style="margin-top:0.4rem; font-size:0.75rem;">All answers are exam-oriented. Read thoroughly for best results. Best of luck! 🎯</p>
</footer>

<script>
  function toggle(header) {
    const acc = header.closest('.accordion');
    acc.classList.toggle('open');
  }

  function switchTab(name) {
    document.querySelectorAll('.panel').forEach(p => p.classList.remove('active'));
    document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
    document.getElementById('panel-' + name).classList.add('active');
    event.currentTarget.classList.add('active');
    window.scrollTo({ top: 0, behavior: 'smooth' });
  }
</script>

</body>
</html>
