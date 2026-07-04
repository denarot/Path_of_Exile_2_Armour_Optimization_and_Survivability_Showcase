# PoE2 Armour Optimization & Survivability Analysis

A quantitative framework for Path of Exile 2 single-hit physical survivability, comparing the **Shaman**, **Smith of Kitava**, and **Witchhunter** ascendancies. Includes a full analytical paper and an interactive browser-based calculator.

---

## Files

| File | Description |
|---|---|
| [`shaman_vs_smith.md`](shaman_vs_smith.md) | Full analytical paper (7 sections + appendices) |
| [`PoE2_Armour_Lab.html`](PoE2_Armour_Lab.html) | Interactive armour optimizer — open in any browser, no server needed |

---

## The Paper

Derives the PoE2 armour DR formula from first principles, identifies the optimal 12–20×L armour corridor for zero-conversion builds, then shows how physical-to-elemental conversion mechanics fundamentally change the calculus.

**Key results:**

- **Shaman (75% conversion, 90% max fire res):** zero armour covers the physical residual at any combined pool ≥ 2,500 HP; full survival (including the fire component) requires a combined pool (life + ES) of ≥ 3,175 at 90% fire resistance against a 10,000 raw ceiling
- **Smith of Kitava (35% conversion):** Internal Layer + Blade Catcher produce a hit at base damage defended with 2× armour on every crit — converting the most dangerous map modifier into a structural advantage; Dedication to Kitava provides the only native armour-applies-to-chaos in the class lineup
- **Witchhunter (Sorcery Ward):** two ascendancy notables convert armour and evasion into a flat absorption pool covering all hit types; survival ceiling at mid-endgame investment approaches H ≈ 14,485 raw physical — higher than either conversion build at comparable gear investment, with no unique-item dependency

**Mathematical proofs included:**
- The 23.4 pp structural DR gap between Shaman and Smith at any armour value (independent of armour level)
- Exact proof that halving a hit via 50% conversion is always precisely 2× more mitigation-efficient than doubling armour, at every hit size and every armour value
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
- Table values were verified by running Python calculations in-session and cross-checking against the formulae; one Smith of Kitava value (H=12,500, A=50k) was corrected from a wrong figure that had propagated across two sections
- The Witchhunter analysis and ecological niche synthesis were added in a later session, extending the paper beyond its original two-build scope

The methodology demonstrates that the most valuable prompting skill is not knowing the right questions to ask in advance — it is knowing when an answer is wrong, insisting on precision, and iterating to correctness.

---

## License

MIT
