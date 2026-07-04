# Shaman vs Smith of Kitava: Defensive Efficiency Across the Hit Damage Spectrum
### A Cost–Benefit Analysis at Achievable Armour Values
*Path of Exile 2 — Cross-Archetype Mitigation Theory · June 2026*

---

## 0. Executive Summary

**1. Methodological Approach**

Two comparative frameworks establish the relative defensive standing of the Shaman, Smith of Kitava (SoK), and Witchhunter ascendancies. Option 1 calculates the equivalent armour value a Smith of Kitava would require to match the Shaman’s physical damage reduction at a given life pool — illustrative, but incomplete as a measure of efficiency. Option 2 holds armour constant across both classes and isolates the percentage-point differential in resultant physical DR. This method exposes the structural source of Shaman’s advantage and reveals the regimes in which Smith and Witchhunter invert it. A third framework — Sorcery Ward pool sizing — is introduced for the Witchhunter, which replaces DR-based survival analysis with an absorption-layer model. The unifying constraint: armour targets an armour-to-life ratio of 12–20×L only for zero-conversion builds. All three archetypes examined here use conversion or absorption mechanics that fundamentally alter what that ratio means in practice.

**2. Quantitative Gap and Opportunity Cost**

At equivalent armour values (A = 50,000), Shaman’s physical DR advantage over Smith converges to a structural maximum of **23.4 percentage points**, independent of armour level. The gap does not close at any finite armour value because additional armour raises both builds’ DR curves in parallel; only the conversion fraction determines the ceiling. The total damage taken ratio is **3.0–3.4×** (Smith worse) across the endgame-relevant hit range, peaking in the 2,000–4,000 raw band. Smith’s corrected armour requirement at a 10,000 raw ceiling ranges from 40,625 (at 4,000 HP) to 75,833 (at 3,000 HP); Shaman’s requirement at the same ceiling is zero for any life pool above 2,500 HP — for the physical component. The critical qualification: at zero armour, Shaman’s fire component adds 675–1,013 damage on a 10,000 raw hit (depending on whether fire resistance is 90% or 85%). The full survival target is a combined pool (life + Energy Shield) of **≥3,175** at 90% maximum fire resistance, not the life figure alone. The passive-point budget freed by Shaman’s zero-armour physical floor — 8–15 nodes plus chest affixes — is reallocated without defensive trade-off into life, Energy Shield, or offensive investment.

**3. Driver of the Performance Differential**

The observed defensive gap is not attributable to armour magnitude or passive-node count. It is driven entirely by **conversion fraction**: the mechanic by which a percentage of physical damage taken is redirected as elemental damage before the armour formula evaluates. At 75% conversion, Shaman’s armour formula evaluates against 0.25H rather than H — a 4× reduction in effective hit size that compounds quadratically in the damage-taken expression (H²_eff). No amount of armour stacking closes this gap because armour appears in both the numerator and denominator of the DR formula; conversion removes input from the formula entirely.

**4. Contextual Inversion: Niche Counter-Cases**

Three narrowly defined conditions invert or substantially narrow the general ranking. First, on **critical-strike maps**, Smith’s Internal Layer (100% reduced crit damage bonus) combined with Blade Catcher (armour doubles on crits) produces a hit at base size defended with twice the armour — strictly better than a standard map. Shaman, with no crit-specific mechanic, receives the full 2× multiplied hit. The damage ratio inverts: Smith takes 1.2–1.7× less than Shaman on crits. Second, **chaos damage** bypasses Shaman entirely (no conversion layer, no chaos mitigation beyond resistance) while Smith applies full armour DR via Dedication to Kitava. At 50% chaos resistance and a 3,500 HP pool, Smith survives an 8,000 chaos hit (2,462 taken); Shaman does not (4,000 taken). Third, **Witchhunter’s Sorcery Ward** extends the physical one-shot ceiling beyond what either Shaman or Smith can achieve at comparable investment: a mid-endgame Witchhunter (60,000 geared armour, SW = 9,000, L = 3,000) survives a 10,000 raw physical hit with zero life damage taken, while both Smith and Shaman at L = 3,000 are structurally fatal without additional Energy Shield.

**5. Prescriptive Recommendation**

All three archetypes are viable and each occupies a distinct defensive niche. *Shaman*: target a combined pool of ≥3,175 HP+ES at 90% maximum fire resistance to survive the 10,000 raw ceiling at zero armour; surviving the fire component is the operative constraint, not the physical one. *Smith of Kitava*: size armour to the raw-hit ceiling of intended content using the §7.1 table, not a fixed multiple of life; mandatory Internal Layer and Dedication to Kitava; most efficient at life pools ≥3,500. *Witchhunter*: two ascendancy notables (Obsessive Rituals + Ceremonial Ablution) replace the armour-sizing problem with a Sorcery Ward pool that covers physical, elemental, and chaos in sequence, with no unique-item requirement; survival ceiling at mid-endgame investment approaches H = 14,485 against a raw physical hit. Class selection should be driven by the threat profile of the content being farmed, not by generalised heuristics.

---

## 1. Introduction

I. Introduction
The central question guiding this inquiry is deceptively simple: How much armour is sufficient, and at what point does additional armour cease to confer meaningful defensive value? While the Path of Exile 2 community has produced numerous heuristics—most commonly "as much as possible"—a rigorous, quantitative answer remains conspicuously absent from the extant literature. Prevailing practice typically involves maximising armour alongside life and strength affixes, often producing characters with formidable raw statistics that nonetheless operate below the Pareto frontier of defensive optimisation.

Consider, for illustrative purposes, a widely cited Titan build featuring 72,000 armour, 4,000–5,000 effective HP (eHP), and approximately 60% block chance (augmented via The Anvil). This character is conventionally regarded as "good," and by many metrics it is. Yet, from first principles, it is demonstrably sub-optimal. The armour damage‑reduction formula imposes a fundamental constraint: achieving the 90% physical damage reduction (PDR) cap against a hit of magnitude H requires armour equal to 100 × H—a value that is categorically infeasible against meaningfully large end‑game strikes. More critically, even if the PDR cap were attained, it confers no survival benefit if the residual damage exceeds the character's life pool. A simple illustration suffices: a character with 100 HP and 90% PDR reduces a 1,000‑damage hit to 100 residual damage, and dies nonetheless.

This observation yields a corollary of first‑order importance: there exists an optimal ratio between armour and eHP, not a simple maximisation of either variable in isolation. Stacking armour without proportionate eHP leaves the character vulnerable to one‑shots; stacking eHP without armour leaves the character equally exposed. The relationship is thus governed by a distribution curve that, for any given eHP pool, defines a minimum and maximum armour value that jointly satisfy near‑optimal survivability. The lower bound of this interval is approximately 12×eHP: beneath this threshold, each point of armour returns more survivability than the equivalent investment in life, so armour acquisition is preferred. The upper bound is approximately 20×eHP: beyond this threshold, the marginal armour point underperforms the equivalent point of eHP, and any surplus is better redirected toward expanding the life pool while holding armour constant. Between these bounds lies the near-optimal corridor in which armour and eHP are jointly balanced.

The present paper pursues three interconnected objectives. First, it formalises the armour formula and derives the optimal armour‑to‑eHP ratio range for maximising physical damage reduction. Second, it quantifies the efficiency gains achieved by converting a fraction of physical damage taken to elemental damage—specifically, the Shaman's physical‑to‑fire conversion mechanic—and positions this within the passive‑point economy as a superior efficiency frontier. Third, it demonstrates that certain armour values, while mathematically illustrative, are practically unattainable; their inclusion serves to expose the futility of attempting to match conversion‑based defence through raw armour stacking, particularly when the opportunity cost—measured in passive points foregone from offensive scaling—renders the resulting character non‑viable in clear speed and damage output.

To ensure a controlled comparison, armour values are held fixed across both ascendancy classes examined (Shaman and Smith of Kitava). This methodology isolates the differential contribution of conversion mechanics and reveals the residual hit size each build can withstand, along with the corresponding eHP required to survive a near‑fatal physical one‑shot. Critically, this analysis demonstrates that neither class is universally superior; rather, each possesses categorical advantages contingent upon content type, threat distribution, and mechanical niche. While the author's preference favours the Shaman—on grounds of elegance, scaling efficiency, and superior damage‑node accessibility—the guiding principle advanced herein is that class selection should be driven by the specific threat profile of the content the player intends to run, not by generalised heuristics.

This paper does not prescribe a single "correct" class. It instead provides a framework for evaluating optimal builds conditional on class choice, and it tempers expectations regarding realistically achievable defensive benchmarks. A common source of player disappointment is the mistaken belief that a "ridiculous" armour value confers proportional survivability; in reality, armour scales linearly or logarithmically with investment, while its marginal contribution to damage reduction decays quadratically against increasing hit sizes. By the formula's own logic, the higher the incoming hit, the less worthwhile additional armour becomes.

II. Paper Structure
The remainder of this paper is organised as follows:

Introduction (above) – framing the research question and motivating the analysis.

Mathematics & Methodology – presenting the armour formula, the survival condition, the derivation of the soft‑cap rule, the conversion and residual‑hit mechanics, the Smith of Kitava defensive profile (with supporting data in Appendix D), and the build parameters used throughout the comparative analysis.

Analysis – comprising five sub‑sections: Physical Damage Reduction (§3.1, comparative PDR across classes at equal armour); Physical Damage Taken (§3.2, residual damage totals); The Asymptotic Gap (§3.3, the structural 23.4 pp ceiling); Three‑Scenario Damage Taken (§3.4, physical non-crit, crit map, and chaos); and Smith of Kitava Armour Bounds by Life Pool (§3.5, content-ceiling survival table).

When Shaman Wins – examining the residual‑hit floor (§4.1), passive‑point economy (§4.2), hit‑size‑agnostic survivability and the corrected zero-armour pool target (§4.3), cross-archetype eHP comparison (§4.4), and the Cloak of Flames universal conversion floor with its mathematical proof (§4.5).

When Smith of Kitava Wins – analysing the neutralisation of critical‑strike maps (§5.1), chaos one‑shot prevention via Dedication to Kitava (§5.2), the economic niche of the SoK (§5.3), and a summary of value proposition (§5.4).

Comparative Analysis – re-pinning armour bounds to a raw-hit ceiling (§6.1), interpreting the damage-taken table at the survival boundary (§6.2), the deciding factor restated (§6.3), and the Witchhunter Sorcery Ward structural aside (§6.4).

Conclusion & Recommendations – recommended minimum armour by build, life pool, and content ceiling (§7.1), a formal decision rule for all three archetypes (§7.2), and a closing discussion of ecological niche and build viability (§7.3).

Appendices – full workbook tables (A), interactive dashboards (B, C), mechanic sourcing (D), and the physical damage reduction reference matrix (E).

---

## 2. Math & Methodology

### 2.1 The armour formula

Path of Exile 2 mitigates a physical hit of size *H* against armour rating *A* by:

$$DR_{phys} = \min\left(0.90,\ \frac{A}{A + 10H}\right)$$

Damage taken is therefore:

$$\text{taken} = H\,(1 - DR) = \frac{10H^2}{A + 10H}\quad(\text{below the cap})$$

The quadratic *H²* in the numerator against a linear *H* in the denominator is
armour's structural weakness: damage taken grows quadratically with hit size
while armour sits linearly. The only way to counteract it without raising *A* (armour value)
is to reduce *H* (base hit value).

Damage reduction layers apply in sequence: armour DR reduces the raw hit first, then elemental or chaos resistance reduces the post-armour remainder, and flat *less damage taken* modifiers apply last as a multiplier on the post-resistance value.

### 2.2 Survival condition and the soft-cap rule

For a life pool *L* (eHP), survival of a single hit requires the hit taken to be  ≤ *L*. Solving for
the armour required:

$$A^* = \frac{10H(H - L)}{L}$$

Two consequences: if *H ≤ L* then *A\* ≤ 0* (the hit cannot kill, armour is pure
comfort); and substituting *H = kL* collapses the constant-*L* dependence into a
pure ratio — *A\* = 10k(k−1)·L*. This yields the rule-of-thumb caps:

- **Soft cap** (covers a 1.7× hit): *A\* ≈ 12 × L*
- **Hard cap** (covers a 2.0× hit): *A\* = 20 × L*

**Corollary — life dominates armour past the hard cap.** From A\* = 10H(H−L)/L, the partial derivative with respect to *L* is ∂A\*/∂L = −10H²/L², which is strictly negative and grows in magnitude as L² shrinks. Armour requirements therefore fall *faster than linearly* as *L* grows: raising *L* from 3,000 to 3,500 HP reduces A\* by more than 17% because both the numerator term (H−L) and the denominator L respond simultaneously. Every point of life past the hard-cap threshold achieves two things no point of armour can: it raises the kill threshold (larger hits become sub-lethal outright) and it reduces the armour floor for the current content tier. This is the structural reason increasing *L* is more efficient than stacking armour once the 12–20×L corridor is met.

### 2.3 Conversion and the residual hit

Conversion of a fraction *c* of physical damage to elemental means the armour
formula evaluates against only the residual physical, *H_eff = (1 − c)·H*.
Substituting into §2.2:

$$A^*_{\text{conv}} = \frac{10(1-c)H\,\big((1-c)H - L\big)}{L}$$

**Key result (Shaman, c = 0.75):** the residual is *0.25H*, so the formula sees a
4× smaller hit. But because *L* does not shrink with the hit, the armour
requirement does **not** simply divide by 4 — it falls *faster* near the
threshold. The residual exceeds *L* only when *0.25H > L*, i.e. **raw hit > 4×L**.
Below that, the Shaman needs *zero* armour for physical survival.

### 2.3a Conversion-dependence of the armour-bound rule

The 12×L–20×L corridor derived in §2.2 is frequently misread as a universal target applicable to any build. It is not. The multipliers 12 and 20 emerge from the survival formula evaluated against the residual hit under the implicit assumption that no conversion is present — residual equals raw. Once a class converts a fraction *c* of physical damage to another type, the corridor must be recomputed against *(1−c)·H*, exactly as performed for the Shaman in §2.3. Applying the raw-hit corridor to a converting class double-counts the armour requirement.

Two framings clarify the correction. If the threat is expressed as a ratio *k = H/L*, conversion collapses the armour requirement quadratically: a 2.0× raw hit becomes a 1.3× effective hit at 35% conversion, and *A\* = 10·k_eff(k_eff − 1)·L* falls from 20×L to approximately 3.9×L. If instead the threat is expressed as a fixed raw ceiling — the physically meaningful framing, since a monster strikes for an absolute damage value independent of the defender's life pool — the requirement scales with that ceiling and does not collapse to a single multiplier. The ratio framing flatters conversion builds; the raw-ceiling framing is the one a player should plan against.

### 2.4 Smith of Kitava mechanics (sourced — see Appendix D)

| Mechanic | Effect on the formula |
|---|---|
| Internal Layer | 100% reduced crit damage *bonus* → crit lands at base hit size (multiplier → 1×), still flagged as a crit |
| Blade Catcher | Defend with 200% of armour vs crits → *A → 2A* on critical hits |
| Dedication to Kitava | Armour applies to chaos hits → chaos uses *DR = A/(A+10H)* instead of landing raw |

Crit damage taken for Smith:
$$\text{taken}_{crit} = H_{eff}\cdot m \cdot \left(1 - \frac{2A}{2A + 10 H_{eff} m}\right),\quad m = 1 + (M-1)(1 - r_{IL})$$
where *M* is the base crit multiplier (2.0) and *r_IL* the Internal Layer
reduction (1.0). With *r_IL = 1*, *m → 1*: the crit multiplier is neutralized
**and** armour doubles.

### 2.5 Build parameters

Both builds are held at identical armour in all §3 comparisons. Every mitigation difference observed in §3–6 is attributable exclusively to conversion fraction and build-specific mechanics, not to armour scaling.

| Parameter | Shaman | Smith of Kitava |
|:---|:---|:---|
| Life pool | 2,000–4,000 (tables grid) | 2,000–4,000 (tables grid) |
| Armour (A) | Equal — held constant | Equal — held constant |
| Physical-to-fire conversion (*c*) | 75% | 35% |
| Residual physical fraction (1−*c*) | 0.25 | 0.65 |
| Fire resistance | 90% maximum | 90% maximum |
| Armour applies to elemental (fire) | Yes | Yes |
| Chaos resistance | None assumed | None assumed |
| 10% less elemental damage taken | Yes | No |
| Adaptive 20% less damage taken | Yes — excluded from calculations (see note) | No |

**Shaman elemental reduction.** Shaman has two stacking layers of elemental damage reduction beyond resistance:

- *Permanent — applied in all calculations:* 10% less elemental damage taken. Applied after armour and resistance as a flat multiplier on the post-resistance remainder. All Shaman fire-component figures in §3 and §6 reflect this modifier.
- *Adaptive — excluded from calculations:* 20% less damage taken based on the highest damage type received in the prior 5 seconds. In practice this activates as 20% less fire damage on any successive hit that follows within 5 seconds of a physical-fire hit. Because the 5-second window expires between isolated spike hits, treating it as permanent would overstate mitigation in single-hit scenarios; it is therefore excluded from all tables. In a sustained volley where hits arrive within the 5-second window, the combined elemental multiplier is ×0.90 × 0.80 = ×0.72 — meaning the post-resistance fire component is 28% lower than the table values show, and Shaman's volley survivability margin is correspondingly wider.

---

## 3. Analysis

*Neutral head-to-head at equal armour. No verdict yet — these are the numbers
both sides argue from in §4–5.*

### 3.1 Physical damage reduction

Both builds share A = 50,000 armour. DR applies to each build's physical residual: Shaman H_eff = 0.25H; Smith H_eff = 0.65H. Cells at the 90% cap are marked †; the gap is compressed or masked in that region.

| Raw hit (H) | Shaman DR | Smith DR | Δ (pp) |
|---:|---:|---:|---:|
| 1,000 | 90.0% † | 88.5% | — |
| 2,000 | 90.0% † | 79.4% | — |
| 3,000 | 87.0% | 71.9% | 15.1 |
| 4,000 | 83.3% | 65.8% | 17.5 |
| 6,000 | 76.9% | 56.2% | 20.7 |
| 8,000 | 71.4% | 49.0% | 22.4 |
| 10,000 | 66.7% | 43.5% | 23.2 |
| 12,500 | 61.5% | 38.1% | **23.4** ← gap peaks |

*The peak gap of 23.4 pp occurs at H ≈ A/4 and is independent of armour level (see §3.3).*

### 3.2 Total damage taken

Both builds share A = 50,000. Values are total damage taken: physical residual (after armour) plus fire component (after armour and 90% fire resistance). Shaman values additionally apply the permanent 10% less elemental modifier (§2.5); the adaptive 20% layer is excluded. The 90% DR cap applies independently to each component.

| Raw hit (H) | Shaman taken | Smith taken | Smith / Shaman |
|---:|---:|---:|---:|
| 1,000 | 34 | 78 | 2.3× |
| 2,000 | 81 | 277 | 3.4× |
| 4,000 | 268 | 920 | 3.4× |
| 6,000 | 538 | 1,771 | 3.3× |
| 8,000 | 866 | 2,752 | 3.2× |
| 10,000 | 1,238 | 3,818 | 3.1× |
| 12,500 | 1,752 | 5,234 | 3.0× |

*The ratio narrows at very small hits (both near-capped) and at very large hits (both DRs collapse). It peaks around 3.4× in the mid-range that defines survivable endgame content.*

### 3.3 The asymptotic gap

The DR gap between Shaman and Smith is not constant but has a structural maximum that is independent of armour. Define the gap as a function of hit size:

$$\Delta(H) = \frac{A}{A + 2.5H} - \frac{A}{A + 6.5H} = \frac{4AH}{(A+2.5H)(A+6.5H)}$$

Setting dΔ/dH = 0 and solving gives the peak at:

$$H^* = \frac{A}{\sqrt{2.5 \times 6.5}} = \frac{A}{4.031}$$

Substituting H\* back yields a maximum gap that simplifies to a function of the residual fractions only:

$$\Delta_{\max} = \frac{1}{1 + r_{sha}\sqrt{r_{smith}/r_{sha}}} - \frac{1}{1 + r_{smith}\sqrt{r_{sha}/r_{smith}}}$$

where r_sha = 0.25 and r_smith = 0.65. Numerically: DR_shaman at H\* = 61.7%, DR_smith = 38.3%, giving Δ_max = **23.4 pp**. This value is independent of armour: at A = 30k the peak occurs at H ≈ 7,400; at A = 70k it occurs at H ≈ 17,400. The gap itself is always 23.4 pp at that hit size. Adding armour shifts the peak hit size upward but does not alter the peak gap.

The practical consequence: at any armour level within the endgame-achievable range, Smith's DR trails Shaman's by up to 23 pp in the hit-size band that most threatens survival. No finite armour investment closes this gap, because additional armour raises both builds' DR curves in parallel.

### 3.4 Three-scenario damage taken

**Physical (non-crit):**

A = 50,000 throughout. Values are total damage taken (physical residual after armour + fire component after armour, 90% fire resistance, and Shaman's 10% less elemental modifier). Reproduced from §3.2.

| Raw hit (H) | Shaman taken | Smith taken | Smith / Shaman |
|---:|---:|---:|---:|
| 1,000 | 34 | 78 | 2.3× |
| 2,000 | 81 | 277 | 3.4× |
| 4,000 | 268 | 920 | 3.4× |
| 6,000 | 538 | 1,771 | 3.3× |
| 8,000 | 866 | 2,751 | 3.2× |
| 10,000 | 1,238 | 3,818 | 3.1× |
| 12,500 | 1,752 | 5,234 | 3.0× |

**Crit map:**

On a critical-strike map, Smith's Internal Layer reduces the crit bonus to zero (the crit lands at base hit size H) and Blade Catcher doubles effective armour (A → 2A = 100,000). Shaman has no crit-specific mechanic: it receives the full crit hit M × H, where M = 2.0 (§2.4 baseline). The *Base hit (H)* column is the underlying non-crit strike. Non-crit columns are reproduced from §3.2 for comparison; the crit columns show the same content if critical strikes land.

| Base hit (H) | Shaman non-crit | Shaman crit (at 2H) | Smith non-crit | Smith crit (H at 2A) | Shaman / Smith (crit) |
|---:|---:|---:|---:|---:|---:|
| 1,000 | 34 | 81 | 78 | 68 | 1.2× |
| 2,000 | 81 | 268 | 277 | 157 | 1.7× |
| 4,000 | 268 | 866 | 920 | 554 | 1.6× |
| 6,000 | 538 | 1,646 | 1,771 | 1,131 | 1.5× |
| 8,000 | 866 | 2,540 | 2,752 | 1,840 | 1.4× |
| 10,000 | 1,238 | 3,512 | 3,818 | 2,651 | 1.3× |
| 12,500 | 1,752 | 4,804 | 5,234 | 3,775 | 1.3× |

*The advantage fully inverts on a crit map. Smith's crit-scenario damage is 13–43% lower than its non-crit figure (Blade Catcher doubling armour and Internal Layer eliminating the bonus combine into a net improvement on every critical hit). Shaman's crit-scenario damage is 2.4–3.3× its non-crit figure (no mitigation for the multiplied hit). The ratio column, Shaman / Smith, was 3.0–3.4× (Smith worse) on non-crits; it becomes 1.2–1.7× (Smith better) on crits. Smith's advantage peaks at H = 2,000 base (doubled armour exits the 90% DR cap zone while Shaman's doubled-hit pushes further into low-DR territory) and narrows gradually at larger hit sizes as conversion's contribution to Shaman's mitigation grows.*

**Chaos:**

Chaos hits bypass Shaman's physical-to-fire conversion (conversion is physical-damage specific) and land with no armour reduction. Smith applies its full armour to chaos hits via Dedication to Kitava: DR_chaos = A/(A+10H) at A = 50,000. Both builds then apply their chaos resistance as a final multiplier. Reference pool: 3,500 HP. Full breakpoint analysis in §5.2.

| Chaos res | Build | 1k hit | 4k hit | 8k hit | 10k hit |
|---:|:---|---:|---:|---:|---:|
| **0%** | Shaman | 1,000 | 4,000 † | 8,000 † | 10,000 † |
| | Smith | 167 | 1,778 | 4,923 † | 6,667 † |
| **25%** | Shaman | 750 | 3,000 | 6,000 † | 7,500 † |
| | Smith | 125 | 1,333 | 3,692 † | 5,000 † |
| **50%** | Shaman | 500 | 2,000 | 4,000 † | 5,000 † |
| | Smith | 83 | 889 | 2,462 | 3,333 |
| **75%** | Shaman | 250 | 1,000 | 2,000 | 2,500 |
| | Smith | 42 | 444 | 1,231 | 1,667 |

*† Damage exceeds 3,500 HP reference pool. Smith wins decisively at all resistance tiers; the absolute damage advantage is largest at 0% resistance and scales proportionally with resistance on both sides (§5.2).*

### 3.5 Smith of Kitava — armour bounds by life pool

Build parameters: 35% physical-to-fire conversion, armour applies to elemental damage, 90% fire resistance. Armour columns are stated as multiples of the life pool *L* followed by the absolute value at each life tier. Figures are total damage taken (physical and fire components combined after all mitigation). Cells where damage taken exceeds the life pool are marked †.

| Life pool | Armour | 1k hit | 2k hit | 4k hit | 8k hit | 10k hit |
|:---|:---|---:|---:|---:|---:|---:|
| **2,500 HP** | 12×L — 30k (soft cap) | 119 | 406 | 1,252 | 3,433 † | 4,636 † |
| | 20×L — 50k (hard cap) | 78 | 277 | 920 | 2,751 † | 3,818 † |
| | 24×L — 60k (2× soft) | 68 | 239 | 813 | 2,503 † | 3,509 † |
| | 40×L — 100k (2× hard) | 68 | 157 | 554 | 1,840 | 2,651 † |
| **3,000 HP** | 12×L — 36k | 103 | 356 | 1,130 | 3,195 † | 4,356 † |
| | 20×L — 60k | 68 | 239 | 813 | 2,503 | 3,509 † |
| | 24×L — 72k | 68 | 206 | 713 | 2,259 | 3,198 † |
| | 40×L — 120k | 68 | 137 | 478 | 1,625 | 2,363 |
| **3,500 HP** | 12×L — 42k | 91 | 317 | 1,029 | 2,989 | 4,108 † |
| | 20×L — 70k | 68 | 211 | 728 | 2,296 | 3,246 |
| | 24×L — 84k | 68 | 181 | 635 | 2,058 | 2,939 |
| | 40×L — 140k | 68 | 137 | 421 | 1,455 | 2,131 |
| **4,000 HP** | 12×L — 48k | 81 | 286 | 945 | 2,807 | 3,887 |
| | 20×L — 80k | 68 | 189 | 659 | 2,121 | 3,020 |
| | 24×L — 96k | 68 | 162 | 572 | 1,890 | 2,718 |
| | 40×L — 160k | 68 | 137 | 377 | 1,317 | 1,941 |

*† Damage taken exceeds life pool.*

Three observations follow directly from the table. First, the 20×L hard cap is the meaningful survival target: at every pool size, the 20×L column is the first that keeps a 10k hit survivable at 3,500+ HP. Second, because 35% of the incoming hit converts to fire and is mitigated separately by both armour and 90% fire resistance, Smith's effective armour requirement to survive a given hit is somewhat lower than the pure-physical 12–20×L rule implies — the conversion provides a modest additional buffer that the pure-physical derivation in §2.2 does not capture. Third, doubling armour past the hard cap (24×L and 40×L columns) produces steeply diminishing survival returns relative to the same investment applied to *L*.

---

## 4. When Shaman Wins

*Emphasis: passive-point economy and near-zero defensive node investment.*

### 4.1 The residual-hit floor

The zero-armour kill floor established in §2.3 is the most practically consequential result of this paper. Shaman's armour formula evaluates against the residual physical hit only — 0.25H after 75% conversion — and the survival condition A\* ≤ 0 holds whenever that residual does not exceed the life pool: 0.25H ≤ L, equivalently, raw hit ≤ 4×L. At a life pool of 2,500 HP the boundary sits at a 10,000 raw hit; at 3,000 HP it rises to 12,000 raw. No armour, no armour-related passive nodes, and no armour-priority gear affixes are necessary to meet the single-hit physical survival condition against any content that does not produce strikes above this floor.

The final increment on the conversion stack is worth isolating. The cluster that delivers the last 5% of conversion — moving the residual from 30% to 25% of the raw hit — reduces H_eff by approximately one-sixth. Because armour-formula damage taken scales as H²_eff, the compounded reduction in per-hit output is approximately 31% at moderate hit sizes. This single cluster delivers returns disproportionate to its passive-point cost and positions the character at the zero-armour floor.

One inference follows for gear and node selection. Armour applies to elemental damage only insofar as armour is present; a near-zero armour rating applied to the post-conversion fire component adds negligible mitigation on top of the 90% fire resistance and 10% less elemental modifier already in place. The armour-applies-to-elemental mechanic can therefore be deprioritised without meaningful mitigation loss. Energy Shield stacks fully additively with the conversion DR floor and does not compete for armour nodes, making it the natural pool-extension vehicle on this archetype.

### 4.2 Passive-point economy

Armour's survival benefit is concentrated at the kill threshold. Once armour is sufficient to survive the largest lethal hit at a given pool size, additional armour investment reduces damage taken on sub-lethal hits — providing comfort, but no new survival margin. Passive points spent beyond the 12–20×L band produce diminishing returns against the actual threat distribution; the same investment applied to *L* raises the kill threshold proportionally and extends the armour's effective range.

Because Shaman at ≥2,500 HP requires zero armour to survive a 10,000 raw hit, the 8–15 passive points and armour-percentage gear affixes that Smith must commit to reach its armour floor are freed entirely. (The approximately 3×L figure represents only the 2,000 HP edge case; corrected targets across life pools appear in §7.1.) This is not a trade-off: Shaman already out-defends Smith on raw physical at any hit size above approximately 1k raw. The freed budget is a unilateral reallocation into life, resistances, or damage at no defensive cost.

The passive-point efficiency is compounded by the spatial distribution of the relevant nodes on the Druid tree. The three clusters that define the Shaman defensive profile — the mana-before-life node (routing 10% of incoming damage through mana before life), the 5%-physical-to-fire conversion cluster, and the adaptive maximum elemental resistance cluster — all lie along the natural Druid path toward damage and mana investment. Each cluster costs approximately four passive points; a Druid build claims two to three of these as pseudo-mandatory travel nodes without attribute-pathing detours. The opportunity cost of the full defensive profile is therefore near zero: the passive points are already allocated to the natural path.

The accumulated return from those 8–12 pseudo-mandatory points is: roughly 11% effective life expansion from the mana-before-life node; adaptive maximum elemental resistance at or near 85–90% across all elements; and the final conversion increment that completes the zero-armour floor derived in §4.1. The conventional trade-off — defensive nodes purchased against offensive output — does not apply when the defensive nodes lie on the offensive path.

### 4.3 Hit-size-agnostic survivability

The conversion component of DR is independent of hit size. A 500-damage physical hit reaches Shaman as 125 physical plus 34–84 elemental after the permanent 10% less elemental modifier (34 at 90% maximum fire resistance; 84 at the base 75% cap), yielding approximately 68–58% effective DR from conversion alone before any armour contribution. At the §3.5 build assumption of 90% fire resistance, the pre-modifier fire component is 37.5; the 10% less elemental modifier (§2.5) reduces it to 33.75. The same fractional reduction applies at 1k, 5k, and 10k raw: the physical component that armour must evaluate scales proportionally at every magnitude.

Armour's DR collapses as hit size grows because DR = A/(A+10H) → 0 as *H* → ∞. Shaman's DR floor is hit-size-agnostic in a way that armour stacking cannot replicate; the build cannot be physically one-shot at hit sizes that kill Smith precisely because the conversion reduction applies before the armour formula runs. The survival table below quantifies the threshold at each pool size.

Armour required for Shaman to survive a raw physical hit of size H, by life pool. Formula: A\* = 10 × 0.25H × (0.25H − L) / L; result is 0 whenever the residual 0.25H ≤ L (hit cannot kill regardless of armour).

| Life pool (L) | Zero-armour kill floor | H = 8,000 | H = 10,000 | H = 12,000 | H = 15,000 |
|---:|---:|---:|---:|---:|---:|
| 2,000 | H = 8,000 | 0 | 6,250 | 15,000 | 32,813 |
| 2,500 | H = 10,000 | 0 | 0 | 6,000 | 18,750 |
| 3,000 | H = 12,000 | 0 | 0 | 0 | 9,375 |
| 3,500 | H = 14,000 | 0 | 0 | 0 | 3,571 |
| 4,000 | H = 16,000 | 0 | 0 | 0 | 0 |

*"Zero-armour kill floor" = the raw hit at which the physical residual (0.25H) first equals L. Below it, zero armour is sufficient for the physical component. The fire component is taken on top regardless of armour; see note below.*

The table quantifies armour required to keep the physical residual within L. It does not include the fire component, which is present at all armour values. At zero armour against a 10,000 raw hit, the fire component is taken at full armour-reduced value of approximately zero (no armour contribution), leaving 75% of the hit to be reduced by resistance and the less-elemental modifier only: 7,500 × (1 − fire\_res) × 0.90. At 90% fire resistance this is 675; at 85% fire resistance it is 1,013. Total damage taken at A = 0, H = 10,000 is therefore approximately 2,500 + 675 = **3,175** (at 90% fire res) to 2,500 + 1,013 = **3,513** (at 85% fire res). Survival of a 10,000 raw hit at zero armour requires a combined pool (life + Energy Shield) of at least 3,175–3,513, not 2,500.

The practical implication: Shaman's defensive model is not "zero armour is all that is needed" — it is "zero armour covers the physical residual; the fire component requires pool depth." The eHP pool (life + ES) must exceed the total damage taken at the expected hit ceiling. At 90% maximum fire resistance, the total damage fraction at zero armour is 0.25H + 0.0675H = 0.3175H. For a 10,000 raw ceiling, the target pool is approximately 3,175. Each additional 500 HP of pool raises the implied hit ceiling by approximately 1,575 raw — a return that armour investment cannot replicate at these residual-hit magnitudes.

### 4.4 Cross-archetype eHP comparison

Shaman's conversion DR is independent of pool composition. A Life-ES hybrid, a tri-hybrid (Life / ES / Mana), or a pure-life build all evaluate the same 0.25H residual against the total pool; the approximately 68% effective mitigation from conversion and resistance alone is invariant to how that pool is distributed. This architectural flexibility is unique: the DR floor coexists with any pool split the player finds passive-point-efficient, and ES investment scales directly on top of it without competing for the same nodes.

The comparison against the archetypes introduced in §1 is quantifiable. Against a 10,000 raw physical hit at A = 0:

| Archetype | Armour | Damage taken (10k raw hit) | Note |
|:---|---:|---:|:---|
| Shaman (zero armour) | 0 | **3,175** | 0.25H physical + fire after 90% res + 10% less elemental |
| Smith of Kitava | 50,000 | 3,818 | §3.2 table |
| 72,000-armour Titan | 72,000 | ~5,800 | DR = 72k/172k ≈ 42%; physical only, no conversion |
| ES-stacking caster | — | 10,000 | Full hit less applicable resistance; no conversion layer |

A Shaman at zero armour takes less from a 10,000 raw hit than Smith at 50,000 armour, and less than the 72,000-armour Titan introduced in §1 as the conventional "good" defensive benchmark. An ES-stacking caster with 10,000+ ES survives that hit if the pool is sufficient, but absorbs the full magnitude with no reduction — the pool is consumed instead of the hit being shrunk.

The practical consequence: a Shaman with a modest Life-ES pool achieves *functional* eHP — measured in hits of the expected threat magnitude survived — comparable to or exceeding archetypes with materially larger raw pools. The conversion layer eliminates one core character-sheet constraint at near-zero passive cost, which means every point of passive investment that other archetypes direct toward meeting their physical DR floor is, for Shaman, available for offensive or resist targets without internal competition.

### 4.5 Cloak of Flames: the universal conversion floor

The conversion advantage demonstrated in §§4.1–4.4 is not exclusive to the Shaman ascendancy. Cloak of Flames — a unique body armour available to any class — provides 50% of physical damage taken as fire, establishing a conversion baseline of *c* = 0.50. The structural mitigation improvement follows from the same §2.3 derivation, with two differences: fire resistance remains at the standard 75% cap rather than Shaman's 90%, and equipping the unique sacrifices the defensive affixes a high-end chest would otherwise contribute.

**Halving the hit outperforms doubling armour.** The damage-taken formula is quadratic in H_eff but linear in A. From this asymmetry, a precise comparison of the two principal mitigation levers follows:

$$\text{taken}\left(\frac{H}{2},\, A\right) = \frac{2.5H^2}{A+5H} \qquad \text{taken}\left(H,\, 2A\right) = \frac{5H^2}{A+5H}$$

The ratio is exactly **1/2**, independent of H and A. Halving the residual physical hit via 50% conversion always produces exactly half the damage output that doubling armour would — at every hit size and every armour value. Conversion is structurally twice as mitigation-efficient as an equivalent proportional armour increase.

**Comparison: 20×L optimal armour vs Cloak of Flames at conservative armour penalty.** The table fixes L = 3,000 HP and prices the chest slot at 24,000 armour — a deliberately generous estimate of what a high-end body armour contributes to total armour rating. If Cloak of Flames wins under this penalty, the result holds under any plausible chest valuation.

| | Build A — Armour optimal | Build B — Cloak of Flames |
|:---|:---|:---|
| Life pool | 3,000 HP | 3,000 HP |
| Armour | 60,000 (20×L) | 36,000 (12×L — chest penalty applied) |
| Conversion | 0% | 50% physical-to-fire |
| Fire resistance | — | 75% (standard cap) |
| Physical formula | 10H²/(60,000+10H) | 2.5H²/(36,000+5H) |
| Fire formula | — | 0.125H |

| Raw hit (H) | Build A taken | Build A eff. DR | Build B taken | Build B eff. DR | Δ (pp) |
|---:|---:|---:|---:|---:|---:|
| 1,000 | 143 | 85.7% | 186 | 81.4% | A +4.3 |
| 2,000 | 500 | 75.0% | 467 | 76.7% | B +1.7 |
| 3,000 | 1,000 | 66.7% | 816 | 72.8% | B +6.1 |
| 4,000 | 1,600 | 60.0% | 1,214 | 69.7% | B +9.7 |
| 6,000 | 3,000 † | 50.0% | 2,114 | 64.8% | B +14.8 |
| 8,000 | 4,571 † | 42.9% | 3,105 † | 61.2% | B +18.3 |
| 10,000 | 6,250 † | 37.5% | 4,157 † | 58.4% | B +20.9 |

*† Damage taken exceeds L = 3,000 HP.*

Build A's effective DR collapses from 85.7% to 37.5% as hit size grows from 1k to 10k — the armour formula's structural weakness against large hits. Build B holds 58.4% at 10k raw because the fire component shrinks relative to the hit as armour's contribution to the physical portion stabilises. The crossover in effective DR occurs at approximately H = 1,500: below that threshold, Build A's higher armour rating produces lower damage taken on small, sub-lethal hits where survivability is not at stake. Above it — across every hit size that defines endgame lethality — Build B dominates.

**Survival ceiling.** Build A's survival ceiling is exactly 6,000 raw (confirmed by §2.2: A\* = 10×6,000×3,000/3,000 = 60,000). Solving the Build B damage equation for the L boundary yields H ≈ 7,800 raw — a 30% higher ceiling despite holding 24,000 less armour. The conclusion holds even if the chest's armour contribution is overstated: if a realistic chest contributes only 15,000 armour (A = 45,000 for Build A), Build B's survival ceiling still exceeds Build A's.

**The chest-slot trade-off.** Cloak of Flames forgoes the life, attributes, resistance, and armour affixes of a rare chest. For a build that already meets its resistance targets through other slots, and for which the primary survival concern is large physical hits rather than pool magnitude, the affix loss is recoverable and the mitigation gain is not — no rare chest affix combination replicates 50% physical conversion. The trade-off is most favourable at higher life pools, where the survival ceiling improvement from conversion grows while the absolute value of lost chest affixes remains fixed.

**Shaman as the natural extension.** Cloak of Flames establishes that 50% conversion at 75% fire resistance and 24,000 less armour outperforms 20×L optimal armour stacking across the entire endgame-relevant hit range. Shaman extends this by a further 25 percentage points of conversion (to 75% total), raises fire resistance to 90%, applies the 10% less elemental modifier, and reaches the zero-armour floor at ≥2,500 HP. Cloak of Flames is the floor of the conversion argument; Shaman's ascendancy mechanics are the ceiling.

---

## 5. When Smith of Kitava Wins

*Narrow but uncontested: unaffected by critical strikes + critical strikes are defended against with 200% of armour value & 100% of armour applies to chaos damage from hits - these mods brick maps, which provides an efficient and unique farming niche.*

### 5.1 Crit-map neutralization

#### Internal Layer: neutralizing the multiplier

Critical-strike map modifiers are phrased as *+x% to critical damage bonus* — a fixed additive quantity applied at the multiplier phase, not a percentage increase to existing critical damage. Internal Layer's effect, "Hits against you have 100% reduced Critical Damage Bonus," directly cancels this quantity. The critical strike lands at base hit size, equivalent in effective damage to a non-critical hit.

#### Blade Catcher: armour doubling on flattened crits

Because Smith is critically struck rather than immune to critical strikes, Blade Catcher's condition — "Defend against Critical Hits with 200% of Armour" — is satisfied on every critical strike. The result is a hit at base damage value, defended with twice the normal armour rating. The combined interaction produces a crit-map outcome that is strictly better than a standard map for Smith: the incoming hit is unaugmented and the armour defence is doubled. Most other archetypes treat the same modifier as unsafe or unrunnable.

No additional passive investment beyond the two ascendancy notables is required to activate this interaction. Reference the crit scenario table crossover in §3.4.

### 5.2 Chaos one-shot prevention - Dedication to Kitava is a "choice"

Chaos damage bypasses Energy Shield and has no universal mechanical reduction available through the passive tree — chaos resistance caps the percentage mitigated, but acquiring sufficient chaos resistance on gear consumes rare affix slots that compete with offensive investment. Chaos hits are encountered infrequently enough in endgame content that their lethality is systematically underestimated, making them a common source of unexpected one-shots in hardcore.

Dedication to Kitava routes armour onto chaos hits using the standard DR formula. This interaction is unavailable on any other ascendancy, passive node cluster, or unique item in the game; its exclusivity reflects the design team's assessment of its value ceiling. For a Smith build already holding armour at its content-ceiling target (§6.1), the chaos coverage is effectively zero marginal cost: the armour is already present, and the ascendancy point covers a damage type that would otherwise land without mechanical reduction. Dedication to Kitava is the structural answer to a threat category that Shaman, with no chaos layer, cannot address.

The table below quantifies Smith's advantage at four chaos resistance breakpoints. Smith uses DR = A/(A+10H) via Dedication to Kitava; Shaman takes chaos damage raw. Both builds then apply their respective chaos resistance as a final multiplier. A = 50,000 throughout (§2.5 baseline). Cells where damage taken exceeds a 3,500 HP reference pool are marked †.

| Chaos res | Build | 1k hit | 4k hit | 8k hit | 10k hit |
|---:|:---|---:|---:|---:|---:|
| **0%** | Shaman | 1,000 | 4,000 † | 8,000 † | 10,000 † |
| | Smith | 167 | 1,778 | 4,923 † | 6,667 † |
| **25%** | Shaman | 750 | 3,000 | 6,000 † | 7,500 † |
| | Smith | 125 | 1,333 | 3,692 † | 5,000 † |
| **50%** | Shaman | 500 | 2,000 | 4,000 † | 5,000 † |
| | Smith | 83 | 889 | **2,462** | **3,333** |
| **75%** | Shaman | 250 | 1,000 | 2,000 | 2,500 |
| | Smith | 42 | 444 | 1,231 | 1,667 |

*† Damage exceeds 3,500 HP reference pool.*

The proportional Smith advantage (Smith takes approximately 17–67% of Shaman's chaos damage, depending on hit size) is fixed across all four resistance tiers — both builds scale identically with chaos resistance, so the ratio does not change. What does change is the absolute value of damage prevented: at 0% resistance DtK prevents 3,833 damage on a 10,000 chaos hit; at 75% it prevents 833. Dedication to Kitava is therefore most valuable early in the game when chaos resistance has not yet been acquired, and least redundant at 75% resistance where both archetypes survive the same content comfortably.

The survival threshold shift is the more decisive observation: at a 3,500 HP pool, Smith survives an 8,000 chaos hit at 50% resistance (2,462 taken) while Shaman does not (4,000 taken). Both survive at 75% resistance. DtK effectively moves Smith's survival breakpoint one resistance bracket earlier than Shaman's for hits in the endgame threat range.

### 5.3 The economic niche

At high endgame thresholds, map modifiers that substantially elevate incoming critical or chaos damage create a secondary market: builds that cannot safely run a waystone sell it at a discount relative to a clean version of the same tier. The discount scales with the modifier's danger — the more broadly lethal it is, the lower the clearing price.

Smith of Kitava's crit neutralization and chaos coverage remove both restrictions simultaneously, converting a discounted waystone into standard content. The supply of critical- and chaos-heavy waystones at below-market prices is sustained by the same asymmetry: the seller population is larger than the buyer population. This pricing inefficiency persists as long as Smith remains a minority archetype — a structural advantage that requires no additional gear investment to maintain, only correct ascendancy selection.

### 5.4 Summary of VALUE
Smith's combined mechanical profile — crit neutralization via Internal Layer, doubled armour on critical hits via Blade Catcher, and chaos mitigation via Dedication to Kitava — is collectively unavailable to any other ascendancy (Chaos Inoculation builds excepted, which achieve chaos immunity through a separate mechanical path at the cost of life-based recovery). Within content where these modifiers are active, Smith holds a structural defensive advantage that additional armour investment by other archetypes cannot close. The niche is narrow; outside critical and chaos content, Shaman's passive-point economy and hit-size-agnostic DR represent the stronger general case. Within it, Smith is the correct specialist.

---

## 6. Comparative Analysis

*Reconciliation: §4 and §5 into a single content-dependent rule.*

### 6.1 Re-pinning the bounds to a raw-hit ceiling

The §3.5 table expressed Smith's armour at fixed multiples of life (12×L–20×L). That framing silently imports the zero-conversion assumption derived in §2.2 and consequently overstates Smith's armour requirement by as much as a factor of five. Correcting against a fixed raw-hit ceiling and crediting Smith's 35% conversion symmetrically with Shaman's 75% produces the following actual requirements:

| Raw hit ceiling | Smith — 3,000 HP | Smith — 3,500 HP | Smith — 4,000 HP | Shaman (any pool ≥ 2,500) |
|---:|---:|---:|---:|---:|
| 6,000 | 11,700 (3.9×L) | 4,457 (1.3×L) | 0 | 0 |
| 8,000 | 38,133 (12.7×L) | 25,257 (7.2×L) | 15,600 (3.9×L) | 0 |
| 10,000 | 75,833 (25.3×L) | 55,714 (15.9×L) | 40,625 (10.2×L) | 0 |

*Armour required to keep the physical residual component ≤ L. Shaman's 75% conversion reduces a 10,000 raw hit to a 2,500 residual, which any pool at or above 2,500 HP absorbs unaided.*

Three readings follow. At a 6,000 raw ceiling, Smith requires only a fraction of the naive 12×L figure — confirming that earlier drafts overstated the build's investment cost for moderate content. At 8,000 raw, the requirement approaches the naive 12×L range by coincidence, not by rule. At 10,000 raw, the requirement exceeds the naive corridor outright, because Smith retains 65% residual physical and that residual scales steeply with hit size. There is no fixed armour multiple that is correct across the hit spectrum for a partially-converting class.

### 6.2 What the damage-taken table adds

The §3.5 table complements the armour-requirement table by quantifying outcomes on either side of the survival boundary. At Smith's corrected hard-cap armour for a given ceiling, the actual damage taken on the ceiling hit sits at or just below *L* — as the requirement formula intends. What the §3.5 data demonstrates is the behaviour past that cap: the 24×L and 40×L columns show steeply diminishing returns from doubling armour, returns that are smaller in survival terms than raising *L* by the same passive investment. This observation holds regardless of which armour framing is used; once the survival threshold is met, additional armour is better redirected to life.

### 6.3 The deciding factor, restated

Correctly sizing Smith's armour requirement sharpens rather than softens the overall conclusion. At a raw ceiling below approximately 8,000, Smith's true armour requirement is in the single-digit-multiple-of-life range, the build is economical to construct, and its conditional defences — crit neutralisation, chaos coverage — make it a strong specialist at modest investment. At and above a genuine 10,000 raw ceiling, Smith's residual-physical requirement climbs past any comfortable armour budget, and only Shaman's conversion keeps the residual survivable on an ordinary pool.

The entire Smith-of-Kitava case therefore reduces to a single empirical proposition: that the endgame content tier being farmed does not produce raw physical hits in excess of approximately 8,000. If true, Smith is a viable and economical specialist; its corrected armour targets are achievable, its crit and chaos coverage are structural advantages, and its farming niche is real. If false — if the ceiling sits at or above 10,000 for the target content — the archetype is structurally exposed in precisely the regime that defines that endgame, and Shaman's conversion provides a survivability floor that no armour investment can replicate.

This is not a question theory can answer. It is a measurement: the per-tier hit-size distribution that the companion Hit Sampler (Appendix C) is built to estimate. The class comparison, pursued to its conclusion, terminates in the same unmeasured parameter that governs every other defensive question in this analysis.

### 6.4 Witchhunter: armour converted to eHP via Sorcery Ward

The analysis of Shaman and Smith has turned on a single structural failure of armour: damage taken scales as H² against a linear A denominator, so large hits shred armour DR regardless of investment. Witchhunter's ascendancy resolves this differently. Two notables collectively convert armour and evasion ratings from a diminishing-returns DR multiplier into a flat absorption pool that sidesteps the quadratic scaling problem entirely.

**Mechanics.** Obsessive Rituals applies 50% less to both armour and evasion ratings, then grants Sorcery Ward (SW): an absorption pool sized at 30% of the post-penalty combined armour and evasion, capped at 32,000. Ceremonial Ablution extends SW's coverage from elemental hit damage to all hit damage types, including physical and chaos. The damage sequence: armour DR reduces the incoming hit first; whatever passes through is intercepted by SW before reaching life, mana, or Energy Shield. SW recharges fully on a 6-second cooldown, which can be shortened by cooldown recovery rate investment.

**eHP profile at the paper's baseline parameters.** A character with 60,000 geared armour exits Obsessive Rituals with 30,000 effective armour and gains SW = 0.30 × 30,000 = 9,000. At 3,000 HP, the total absorption stack is 12,000 — comparable to a high-investment pure Energy Shield build. To reach the 32,000 SW cap requires a post-penalty armour+evasion pool of approximately 107,000, or approximately 213,000 before the multiplier, confirming that 9,000 is a realistic mid-endgame figure. The 30,000 residual armour still applies standard DR: DR = 30,000/(30,000 + 10H), falling from 75% at H = 1,000 to 23% at H = 10,000. Against hits that exceed DR's coverage, SW absorbs the post-DR remainder before life is reached:

| Raw hit (H) | DR (A = 30k) | Post-DR damage | SW absorbs | Life damage | Survives? |
|---:|---:|---:|---:|---:|:---:|
| 5,000 | 37.5% | 3,125 | 3,125 | 0 | Yes |
| 8,000 | 27.3% | 5,818 | 5,818 | 0 | Yes |
| 10,000 | 23.1% | 7,692 | 7,692 | 0 | Yes |
| 12,000 | 20.0% | 9,600 | 9,000 | 600 | Yes |
| 14,000 | 17.6% | 11,529 | 9,000 | 2,529 | Yes |
| 14,500 | 17.1% | 12,014 | 9,000 | 3,014 | No † |

*A = 30,000 (post-50%-less), SW = 9,000, L = 3,000. † Survival ceiling ≈ H = 14,485 (derived from 10H²/(30,000 + 10H) = SW + L = 12,000).*

Against the same 10,000 raw hit at equal geared investment: Smith (60,000 armour, 3,000 HP) takes approximately 3,509 total — exceeding L, structurally fatal at this pool size (§3.5). Witchhunter takes 0 life damage from the same hit. Shaman at zero armour and 3,000 HP takes approximately 3,175 total (2,500 physical residual + 675 fire at 90% fire resistance) — also exceeding L by 175, structurally fatal at this pool size without additional Energy Shield. All three archetypes at L = 3,000 require pool depth beyond the base life figure to survive a 10,000 raw hit: only Witchhunter achieves this without Energy Shield or unique-item dependency, via SW absorbing the post-DR remainder before it touches life. Witchhunter's survival of the 10,000 hit requires only two ascendancy notables and no unique-item dependency.

**Ecological niche synthesis.** Each archetype occupies a distinct defensive category. Witchhunter holds the highest one-shot ceiling of the three builds — the SW buffer scales with armour and evasion investment simultaneously, and the survival threshold at L = 3,000 approaches H = 14,485 against physical hits, a figure neither Smith nor Shaman at comparable investment can reach. Smith of Kitava occupies the critical-strike and chaos specialisation niche: Blade Catcher's doubling of effective armour on crits is the strongest crit-specific defensive cooldown available, and Dedication to Kitava's chaos coverage is the only native armour-applies-to-chaos in the archetypes examined here. Shaman occupies the passive-point efficiency and opportunity cost niche: the zero-armour physical survival floor reached at ≥2,500 HP (or ≥3,175 combined pool for full coverage including the fire component) frees the largest block of passive points and gear affixes for offensive or pool-expansion reinvestment. The three builds do not compete for the same defensive resource — they answer different threat profiles and gear-progression structures.

**Cross-damage-type coverage.** SW via Ceremonial Ablution absorbs chaos hits using the same pool and the same sequence (armour DR first, SW intercepts the remainder). This is structurally superior to Shaman's zero chaos layer and operates without Dedication to Kitava's requirement. Against a 10,000 raw chaos hit, SW absorbs up to 7,692 post-DR damage before life is reached; chaos resistance then applies as a further multiplier on any overflow. Witchhunter is the only archetype in this paper that achieves baseline absorption against physical, elemental, and chaos hit damage from a single two-notable investment.

**The evasion interaction.** An armour/evasion hybrid benefits doubly from evasion investment: each point of evasion (post-penalty) adds 30% of that value to SW, and evasion provides a hit-avoidance layer that reduces pool consumption rate. At 50% evasion and 50% block, P(attack lands and is not blocked) = 0.25 — 75% of attacks are avoided before the SW pool is engaged. The multiplicative relationship means that reducing the hit-landing probability from 25% to 20% is a 20% reduction in the rate of pool depletion per encounter, which is proportionally large even for a small absolute change in the hit-landing rate.

**Trade-offs.** SW recharges on a 6-second cooldown rather than regenerating continuously; a rapid burst of large hits depletes SW on the first strike and leaves life exposed until the cooldown completes. Damage over time (bleed, poison, ignite) bypasses SW and must be managed through flasks or dedicated mechanics. The 50% less armour multiplier drops effective armour below the 12×L soft cap for a 3,000 HP character (30,000 vs the 36,000 soft cap) — meaning there is structural incentive to invest in armour more aggressively than the soft cap implies, since each additional point simultaneously improves DR and expands the SW pool. An armour+evasion hybrid running a shield achieves the 30,000 armour floor at lower raw armour investment while adding SW from both defensive stats.

**Investment profile.** Obsessive Rituals and Ceremonial Ablution consume half the ascendancy budget; the remaining notables are available for offensive or utility investment within the Witchhunter kit. No unique item is required at any investment stage, making the defensive model fully accessible in Solo Self-Found, Hardcore, and HC-SSF contexts. Because every point of armour investment simultaneously improves DR and expands SW, the build's defensive scaling is internally consistent across the gearing progression with no threshold at which one layer stops contributing to the other.

**Weapon-swap passive efficiency.** Path of Exile 2 allows passive nodes to be allocated to a specific weapon set, becoming active only while that set is equipped. For a Witchhunter running a primary and secondary weapon set, this creates a structural passive-point surplus: nodes allocated to the inactive set cost no passive investment during the active set's operation. In practice, a secondary weapon set can carry the build's defensive or utility nodes — armour scaling, resistances, the SW-contributing clusters — while the primary set runs an entirely offensive passive allocation. The total passive count available to the character effectively exceeds the nominal allocation, because neither set's nodes compete with the other's while they are not simultaneously active. This is the most underexplored efficiency lever available to the archetype. Players who understand and implement weapon-swap passive allocation are operating with a materially larger effective budget than the passive tree count implies.

Two utility nodes are particularly well-suited to the secondary weapon set. **Culling Strike** — kills enemies below a life threshold (typically 10% maximum life) — converts the final 10% of any enemy's health into an automatic execute. Against enemies that would otherwise require two hits, culling effectively compresses two engagements into one, adding approximately 11% kill efficiency across a full pack (10/(100−10) ≈ 11.1%). On boss encounters with regenerating life, the execute eliminates the window during which damage must outpace recovery. **Explode** mechanics — enemies killed explode dealing a percentage of their maximum life as area physical damage — convert every kill into a secondary clear event. Against tightly packed endgame monster density, a single culled or killed enemy propagates damage across the remaining pack without an additional skill cast, compounding clear speed without increasing the active ability count. Allocated to the secondary weapon set, both nodes cost zero primary-set passive investment; the player retains the full primary-set budget for damage and survivability nodes while gaining substantial clear-speed and kill-speed upside on demand.

---

## 7. Conclusion & Recommendations

The paper's central result is that DR = min(0.90, A/(A + 10H_eff)), where H_eff is the portion of the raw hit that armour actually evaluates. Conversion mechanics determine H_eff — Shaman at 75% conversion faces H_eff = 0.25H; Smith at 35% faces 0.65H — and every observable difference in survivability between the two archetypes follows from this single input. The 23.4 percentage-point maximum PDR gap, the 3.0–3.4× total damage ratio, and the order-of-magnitude difference in armour requirements are all downstream of conversion fraction.

Two broader observations close the analysis. First, the 12×L–20×L armour corridor is a zero-conversion rule. Applied to a build with conversion, it over-specifies the requirement — by a factor of ten for Shaman at standard life pools. The practical Shaman target is zero armour against the residual physical at any life pool above 2,500 HP, because conversion reduces H_eff below L before armour runs. Second, life dominates armour past the survival threshold — the formal corollary from §2.2 — and this principle reaches its endpoint in builds with very large effective pools: a character whose effective pool exceeds the raw hit size achieves the same survival outcome as conversion-based DR with zero armour DR. Both paths — conversion and raw pool scaling via Mind over Matter, Energy Shield stacking, or similar mechanics — answer the same equation: keep H_eff below L.

### 7.1 Recommended minimum armour by build, life pool, and content ceiling

Values are single-hit physical survival minimums derived from the corrected A\* formula. Shaman: A\* = 10 × 0.25H × (0.25H − L) / L; result is 0 whenever 0.25H ≤ L (the §4.3 zero-armour kill floor). Smith: A\* = 10 × 0.65H × (0.65H − L) / L (§6.1, crediting 35% conversion). The naïve 12–20×L corridor applies only to zero-conversion builds and is not used here.

| Build | Life pool | ≤6,000 raw ceiling | ≤8,000 raw ceiling | ≤10,000 raw ceiling |
|:---|---:|---:|---:|---:|
| **Shaman** | 2,000 | 0 | 0 | 6,250 (3.1×L) |
| | 2,500 | 0 | 0 | 0 |
| | 3,000 | 0 | 0 | 0 |
| | 3,500 | 0 | 0 | 0 |
| **Smith of Kitava** | 3,000 | 11,700 (3.9×L) | 38,133 (12.7×L) | 75,833 † (25.3×L) |
| | 3,500 | 4,457 (1.3×L) | 25,257 (7.2×L) | 55,714 (15.9×L) |
| | 4,000 | 0 | 15,600 (3.9×L) | 40,625 (10.2×L) |

*† Exceeds practical gearing ceiling; content at this tier is structurally challenging for Smith at any armour budget.*

Four readings follow. First, Shaman at 2,500 HP requires zero armour to survive any single physical hit up to 10,000 raw; the "~3×L" heuristic that appears elsewhere in the literature was calibrated specifically to a 2,000 HP pool at the 10,000 raw ceiling — it overstates the requirement for any build at standard life investment. Second, Smith's armour requirement is not a fixed multiple of life; it scales steeply with the raw ceiling and falls substantially as the life pool rises. Third, the values above are survival minimums: any armour above the threshold reduces damage on sub-lethal hits (comfort) but does not change the kill condition for the ceiling hit itself. Fourth, the survival tables in §3.5 and §4.3 already function as tier-progression checks — when damage taken at the expected ceiling sits below L for the current life pool and armour combination, the build is calibrated for that content.

The content ceiling is player-determined, not fixed by tier alone. The maximum raw physical hit encountered is a function of waystone tier, the number and nature of dangerous modifiers stacked, monster type, and the player's positioning and encounter decisions. Two players running identical waystones can face different effective ceilings. The table above therefore bounds the defence requirement for any *assumed* ceiling rather than prescribing targets by tier. The operative planning question is: "What is the largest single physical hit I expect to encounter?" — which the §4.3 and §3.5 tables answer for both archetypes across the plausible endgame range.

### 7.2 Decision rule

- **Shaman:** Target a combined pool (life + Energy Shield) of ≥3,175 at 90% maximum fire resistance, or ≥3,513 at 85%, to survive the full 10,000 raw ceiling — accounting for both the 2,500 physical residual and the 675–1,013 fire component at zero armour (§4.3). The zero-armour floor for the *physical* component alone requires life ≥2,500; the fire component is always taken on top and requires the pool to exceed the total fraction 0.3175H (at 90% fire res). Below L = 2,500, armour of approximately 3×L covers the residual physical component only; fire remains a separate pool cost. Remaining passive budget: life, Energy Shield, resistances, damage. Hit-size-agnostic physical DR; no chaos mitigation; no structural crit advantage.
- **Smith of Kitava:** Armour sized to the raw-hit ceiling of the intended content tier using the §7.1 table — not a fixed multiple of life. Mandatory Internal Layer and Dedication to Kitava. Life pool ≥3,500 to keep the 8,000 ceiling armour requirement below 26,000. Best for crit-map and chaos content; structurally exposed to raw physical hits above ~8,000 if under-armoured for the ceiling.
- **Witchhunter:** Two ascendancy notables only (Obsessive Rituals + Ceremonial Ablution). No unique item required. Target 60,000 geared armour pre-penalty for a SW pool of 9,000 and a combined absorption stack of 12,000 at L = 3,000; survival ceiling approaches H = 14,485 raw physical at this investment. Evasion investment expands SW simultaneously. Secondary weapon set is the highest-leverage passive-efficiency mechanic available — allocate culling strike and explode nodes here at zero cost to the primary set. Best for: players targeting the highest one-shot ceiling per passive-point invested; HC/HC-SSF viability; all damage-type coverage without unique dependency.
- **The content ceiling determines the recommendation.** The maximum raw physical hit is modulated by waystone tier and modifier selection; it is not observable from theory alone. The §7.1 table, read against the §3.5 and §4.3 survival tables in the paper, provides the calibration without requiring external measurement: identify the ceiling hit expected for the content tier, locate the corresponding life pool and armour row, and verify that damage taken sits below L.

### 7.3 All paths lead to the summit

The three archetypes examined here — Shaman, Smith of Kitava, and Witchhunter — share a low pick rate in the current endgame meta and are routinely undervalued by tier lists calibrated to raw screen-clear speed. This paper's central argument is that pick rate is not a proxy for ceiling power: it is a proxy for *accessibility of the mechanical insight required to reach that ceiling*. Each build demands a specific blend of game-knowledge — conversion fractions, armour-formula nonlinearity, SW pooling — that is non-obvious from passive tree inspection or gear stat tooltips. Players who lack this layer of comprehension will underperform; players who have it are rewarded disproportionately, because the market for these builds is thin and the gear that unlocks them is comparatively affordable.

There are many paths to the top of the mountain, and all three of these builds are genuinely viable paths. Shaman funnels saved defensive passive points into offensive investment with a clarity and efficiency the paper has now made quantitative. Smith of Kitava converts a crit-heavy map modifier pool — which most builds dread — into a structural advantage. Witchhunter extends the survival ceiling further than any life-stacking or armour-stacking approach available to the other classes, at the cost of cooldown dependency. The goal of this analysis is not to declare a winner among them. It is to give any reader who encounters these builds in a guide, a trade whisper, or a video — and wonders whether they are powerful enough to justify the investment — a defensible, quantitative basis for the answer: yes, they are, and here is exactly why.

---

## Appendices

### Appendix A — Full workbook tables
Source of truth: `workbook/mitigation_model.xlsx`. Every table in this paper is
generated from it via `scripts/generate_tables.py`. Change an assumption cell,
recalculate, regenerate — the paper stays consistent.

### Appendix B — Interactive dashboard: Armour Lab
Optimizer + hit-distribution sampler. Open in any browser — no server or install required.
URL: [PoE2_Armour_Lab.html](https://denarot.github.io/Path_of_Exile_2_Armour_Optimization_and_Survivability_Showcase/PoE2_Armour_Lab.html)
Local: download `PoE2_Armour_Lab.html` from the [repository](https://github.com/denarot/Path_of_Exile_2_Armour_Optimization_and_Survivability_Showcase) and open in any browser.

### Appendix C — Interactive dashboard: Shaman vs Smith
The Armour Lab (Appendix B) includes the three-scenario comparison (physical non-crit, crit map with Blade Catcher, chaos with Dedication to Kitava) via the Damage Simulation section and build quick-select presets. A dedicated three-scenario comparison view may be added in a future version.

### Appendix D — Mechanic sourcing

- **Armour formula & 90% cap** — PoE2 community armour guides (mobalytics, vulkk).
- **Blade Catcher** — "Defend with 200% of Armour against Critical Hits, +15 to
  Strength" (poe2wiki Passive:Armour32; mobalytics armour guide confirms it
  doubles armour for crit mitigation).
- **Internal Layer** — "Hits against you have 100% reduced Critical Damage Bonus"
  (Fextralife; buffed from 50% per mobalytics patch notes).
- **Dedication to Kitava** — "Armour also applies to Chaos Damage taken from Hits"
  (Fextralife, sportskeeda, deltiasgaming).
- **Shaman conversion stack** — Cloak of Flame 50% + ascendancy/tree/anoint to 75%.

<!-- DRAFT: convert these to formal citations / footnotes in your preferred
  style, with access dates. -->

### Appendix E — Physical Damage Reduction reference matrix

DR = min(0.90, A / (A + 10H)). Values are percentage physical damage reduced. Cells marked † are at or above the 90% hard cap. Read across a row to see how DR collapses as hit size grows; read down a column to see the diminishing return on additional armour investment.

| Armour (A) | H = 100 | H = 1,000 | H = 2,000 | H = 4,000 | H = 8,000 | H = 10,000 |
|---:|---:|---:|---:|---:|---:|---:|
| **10,000** | 90.0% † | 50.0% | 33.3% | 20.0% | 11.1% | 9.1% |
| **20,000** | 90.0% † | 66.7% | 50.0% | 33.3% | 20.0% | 16.7% |
| **30,000** | 90.0% † | 75.0% | 60.0% | 42.9% | 27.3% | 23.1% |
| **40,000** | 90.0% † | 80.0% | 66.7% | 50.0% | 33.3% | 28.6% |
| **50,000** | 90.0% † | 83.3% | 71.4% | 55.6% | 38.5% | 33.3% |
| **60,000** | 90.0% † | 85.7% | 75.0% | 60.0% | 42.9% | 37.5% |
| **70,000** | 90.0% † | 87.5% | 77.8% | 63.6% | 46.7% | 41.2% |
| **80,000** | 90.0% † | 88.9% | 80.0% | 66.7% | 50.0% | 44.4% |
| **90,000** | 90.0% † | 90.0% † | 81.8% | 69.2% | 52.9% | 47.4% |
| **100,000** | 90.0% † | 90.0% † | 83.3% | 71.4% | 55.6% | 50.0% |

*Two structural observations follow directly. First, the 90% cap is functionally unreachable against hits above H = 1,000 at any gearing-attainable armour value — the cap requires A ≥ 9H, or 90,000 armour against a 10,000 raw hit. Second, the gain from doubling armour (e.g. 30k → 60k) is largest at moderate hit sizes: at H = 4,000, doubling from 30k to 60k improves DR from 42.9% to 60.0% (+17.1 pp); at H = 10,000, the same doubling yields only 37.5% from 23.1% (+14.4 pp). Damage taken scales as H² in the numerator — the formula penalises large hits faster than additional armour can compensate. This is the mathematical foundation of the conversion argument throughout the paper: reducing H_eff via conversion moves the build leftward and downward in this table simultaneously, reaching DR values that armour alone cannot attain at endgame hit sizes.*
