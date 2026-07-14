# PoE2 Defensive Efficiency: Physical Damage Mitigation Across the Ascendancy Spectrum

A quantitative framework for Path of Exile 2 single-hit physical survivability, comparing four ascendancy archetypes — **Shaman**, **Infernalist**, **Witchhunter**, and **Invoker** — benchmarked against the **Smith of Kitava** as the pure-armour reference. Includes a full analytical paper (LaTeX) and an interactive browser-based calculator.

---

## Files

| File | Description |
|---|---|
| [`shaman_analysis.pdf`](shaman_analysis.pdf) | Full analytical paper — read this (42 pages, no LaTeX required) |
| [`shaman_analysis.tex`](shaman_analysis.tex) | LaTeX source — compile with `pdflatex` twice (MiKTeX or TeX Live) |
| [`PoE2_Armour_Lab.html`](PoE2_Armour_Lab.html) | Interactive armour optimizer — open in any browser, no server needed |

---

## The Paper

Derives the PoE2 armour DR formula from first principles, identifies the optimal 12–20×L armour corridor for zero-conversion builds, then shows how each archetype's distinct defensive mechanic changes the calculus.

**Key results by archetype:**

- **Shaman (75% conversion, 90% max fire res):** Zero armour covers the physical residual at any combined pool ≥ 2,500 HP. Full survival including the fire component requires a combined pool (life + ES) of ≥ 3,175 at 90% fire resistance against a 10,000 raw ceiling. Highest passive-point efficiency of any archetype examined.

- **Infernalist (80% conversion + Chaos Inoculation):** Physical-to-chaos conversion combined with CI makes 20% of every hit a categorical zero rather than near-zero. Infernalist Full (80% total conversion + CI) achieves 85.3% mitigation at H=10,000 — surpassing standard Shaman at 80.8% — while providing hard chaos immunity and freeing all life and chaos resistance affixes for Energy Shield.

- **Witchhunter (Sorcery Ward):** Two ascendancy notables (Obsessive Rituals + Ceremonial Ablution) convert armour and evasion into a flat absorption pool covering all hit types. Survival ceiling at mid-endgame investment approaches H ≈ 14,485 raw physical — higher than either conversion build at comparable gear investment, with no unique-item dependency.

- **Invoker (evasion-as-armour + Meditate):** Avoidance-primary architecture: 75–88% of hits are avoided via evasion and block before any mitigation applies. The "...and protect me from harm" ascendancy node unifies evasion rating into the armour pool (effective armour = base armour + evasion × 0.65). Meditate overflows Energy Shield to 1.5× pre-combat, providing a conditional eHP ceiling that exceeds most passive builds.

- **Smith of Kitava (pure armour benchmark):** Internal Layer + Blade Catcher convert critical-strike map modifiers into a structural advantage (crit lands at base damage, defended with 2× armour). Dedication to Kitava provides the only native armour-applies-to-chaos in the class lineup. Structurally exposed to raw physical hits above ~8,000 without very high armour investment.

**Mathematical proofs included:**
- The 23.4 pp structural DR gap between Shaman and Smith at any armour value (independent of armour level)
- Exact proof that halving a hit via 50% conversion is always precisely 2× more mitigation-efficient than doubling armour, at every hit size and every armour value
- Accelerating returns on conversion: each additional 5 pp of conversion is worth more than the last (shrinking denominator)
- Witchhunter survival ceiling derivation from the quadratic A* formula

---

## The Tool

Open `PoE2_Armour_Lab.html` in any browser — no server, no install, no dependencies. Settings persist via `localStorage`.

**Features:**

| Section | What it does |
|---|---|
| Build Quick-Select | One-click presets for Shaman / Smith of Kitava / Cloak of Flames / Witchhunter |
| Character Setup | Life, Mana, ES, MOM% → computes Effective Hit Pool |
| Armour Evaluator | Evaluates any armour vs 12×/20×EHP targets with verdict and volley-threshold pills |
| Damage Simulation | Full conversion model: physical + elemental DR, flat % less elemental modifier, Blade Catcher crit toggle |
| Witchhunter — Sorcery Ward | SW pool sizing, survival table, ceiling derivation |
| Required Armour Optimizer | Back-calculates armour needed for a target DR% against any raw hit |
| Reference Tables | 12×/20×EHP target table + Appendix E DR matrix (armour 10k–100k × hit 100–10k) |

---

## How it was built

This paper and tool were developed collaboratively with Claude (Anthropic) across multiple sessions. The structure of the work reflects a specific use of AI as a quantitative reasoning partner:

- The mathematical framework (A* survival condition, conversion residual derivation, asymptotic gap proof, Cloak of Flames 1/2 ratio proof) was developed iteratively, with the model deriving and the author directing, questioning, and correcting
- The paper corrected its own zero-armour conclusion mid-session: an early draft stated Shaman at 2,500 HP survives a 10,000 raw hit at zero armour — this was identified as incomplete because it ignored the fire component (675–1,013 damage taken on top), and corrected to a total pool target of ≥ 3,175
- Table values were verified by running Python calculations in-session and cross-checking against the formulae
- The paper expanded across sessions from a two-build comparison (Shaman vs Smith) to a four-archetype analysis (Shaman, Infernalist, Witchhunter, Invoker), with each archetype demonstrating a distinct defensive paradigm: conversion, absorption, and avoidance

The methodology demonstrates that the most valuable prompting skill is not knowing the right questions to ask in advance — it is knowing when an answer is wrong, insisting on precision, and iterating to correctness.

---

## License

MIT
