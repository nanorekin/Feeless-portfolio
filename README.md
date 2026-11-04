# Feeless Portfolio

A free, single-file crypto portfolio simulator. Every coin and every price move is made up and generated right in your browser — **not real market data, not real coins, and nothing here is financial advice.**

## Play

- Trade a **30-day season** across six entirely fictional coins, each with its own personality: **STBL** barely moves, **VOLT** trends up with real swings, **RUG** trends down more often than not with the occasional spike — read the volatility, not a real market.
- **Buy** a share of your cash or **Sell** a share of your holdings with one tap, then press **Advance day** to move the market forward. Prices drift and wobble randomly, and roughly 1 in 6 days brings a news event that swings one coin harder in one direction (shown in the log).
- At the end of day 30, your season scores on total portfolio value (cash plus holdings), converting your result into **insight** — win or lose, every season earns at least a little.
- **Research:** spend insight on permanent upgrades (more starting cash, calmer markets, advance warning of event days via Whale Alert, and rewinds to undo a bad day) that apply to every future season.
- **Daily Challenge:** everyone gets the identical 30-day market on a given day, one run per day, with a streak for playing.
- **Get more insight:** playing is always enough on its own. Tipping XNO (same tip card as every other Feeless game) is an optional way to speed that up or say thanks — it has no effect on market odds.
- A **"How to play"** section on the page explains the rules in plain language.

## Determinism

Every season's price path is generated from a seeded PRNG (`mulberry32`-style) running entirely in the browser — never fetched from anywhere. Practice mode seeds itself randomly each run; Daily Challenge hashes the UTC date into the seed, so everyone playing on a given day gets the identical sequence of prices and news events.

## Deploy on GitHub Pages

1. Create a new repository, for example `feeless-portfolio`.
2. Upload `index.html` and `README.md` to the root of the repository.
3. Open **Settings > Pages**, set the source to **Deploy from a branch**, choose `main` and `/ (root)`, then save.
4. After a minute the game is live at `https://<your-username>.github.io/feeless-portfolio/`.
5. Add it to the Feeless Arcade hub's `GAMES` list once it's live.

## Donations

The tip card works the same way as the other Feeless games:

- A `nano:` payment link with the chosen amount, shown as a QR code and an **Open in wallet** button.
- A **Copy address** button.
- An **I've sent it, check** button that asks public Nano nodes whether a matching payment arrived, then credits insight (currently 300 insight per 1 XNO tipped).

To use a different wallet, change `NANO_ADDRESS` near the top of the script in `index.html`. The insight-per-XNO rate is the `INSIGHT_PER_XNO` constant right below it. If the public RPC endpoints in `RPCS` ever block browser requests, point them at your own proxy.

Insight, Research levels, and the Daily Challenge streak are stored in `localStorage`, so progress is local to one browser, same as every other game's supporter unlock.

Add `?selftest` to the URL to expose a `window.__fp` object for automated tests.
