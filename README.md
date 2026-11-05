# Options Bid-Ask Spread: Desk Reality vs. Textbook Theory

> Educational resource explaining what actually determines the bid-ask spread in listed options markets — from both the market maker’s perspective and the informed investor’s perspective.

Textbooks focus on mid-prices and Greeks. On the desk, the **spread** (and how it is shaded for inventory) is one of the most important daily decisions.

**[View the interactive GitHub Pages site →](https://prakharquant.github.io/options-bid-ask-spread/)**

## Why This Matters

The bid-ask spread is the primary way market makers are compensated for providing liquidity and taking risk. It is also one of the largest explicit transaction costs for traders. Understanding what drives it improves both execution quality and the ability to interpret market microstructure signals.

## Core Drivers of the Bid-Ask Spread (Market Maker View)

Market makers quote around a theoretical value (from a volatility surface). The width and asymmetry of the quote compensate for:

### 1. Inventory / Holding Risk
- Gamma risk (especially high in near-term ATM options)
- Vega risk (longer-dated or high-volatility options)
- Residual delta, pin risk, and cross-book exposures
- Desks continuously shade quotes based on current inventory: long → lower the ask to sell; short → raise the bid to buy

### 2. Adverse Selection / Informed Flow Risk
- Risk of trading against better-informed counterparties (news, earnings, superior vol view, large directional flow)
- Spreads widen when order flow looks one-sided or “toxic”, around events, or after non-trading periods
- Classic microstructure component (Glosten-Milgrom style)

### 3. Hedging & Liquidity Costs
- Cost and expected slippage of delta-hedging in the underlying or futures
- Wider underlying spreads or lower underlying liquidity → wider option spreads
- Illiquid single-stock options trade wider than SPX/SPY or large-cap options at similar volatility

### Other Practical Factors
- **Contract liquidity**: volume, open interest, quoted size, balance of flow
- **Moneyness & maturity**: ATM usually tightest in dollar terms; proportional spreads often widen OTM or in low-priced near-term options
- **Volatility regime**: higher realized or implied vol → wider spreads
- **Competition**: more market makers → tighter quotes
- **Capital, position limits, and exchange rules**
- Many desks manage spreads in **volatility space** first, then convert to price

**Simplified mental model**:
```
Spread ≈ Inventory risk cost + Adverse selection cost + Hedging/transaction costs
(adjusted in real time for current inventory, expected flow toxicity, and competition)
```

## Informed Investor Perspective

The informed trader does not set the spread but faces it as a major cost and influences it through their activity.

- Round-trip cost = full spread × 100 × contracts
- Informed flow itself increases the adverse-selection component (so spreads are wider *because* of informed traders)
- Practical considerations:
  - Prefer liquid underlyings and contracts (high volume + open interest, especially ATM or near-ATM)
  - Use limit orders inside the spread rather than always lifting the offer or hitting the bid
  - Size carefully to limit market impact and inventory shading
  - Be aware of time-of-day and event effects (wider at open/close and around catalysts)
  - For multi-leg strategies, the *net* spread across all legs matters
  - Wide spreads make the mid a noisier estimate of fair value (IV, expected move, skew readings become less reliable)

## Project Structure

- `README.md` — overview and key takeaways
- `index.html` — GitHub Pages site with deeper sections and visual layout
- Future expansions: simple calculators, example notebooks, microstructure case studies

## Related Academic & Practitioner Concepts

- Inventory models (Amihud-Mendelson, Ho-Stoll, Avellaneda-Stoikov)
- Adverse selection models (Glosten-Milgrom)
- Option-specific hedging cost / derivative hedge theory
- Empirical findings on option return volatility as a strong spread determinant

## License

Educational use. Content is for learning purposes and does not constitute investment advice.

---

*Built to close the gap between textbook theory and desk reality.*
