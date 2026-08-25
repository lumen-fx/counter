# counter

The classic click counter, scripted in candela.

What it shows:

- Element handles. `get_by_id("bump")` returns a node you can call methods
  on, the same way `document.getElementById` does on the web.
- Per-element event binding. `node.on("click", "on_bump")` sends clicks on
  that one element straight to that one function, which reads better than
  branching inside a shared handler.
- `on_ready` versus `on_start`. `on_start` runs at load, before the tree is
  mounted, so a lookup there finds nothing; `on_ready` runs on the first
  tick, once the elements exist. Bind events from `on_ready`.
- Signals. `lumen::signal_set_int("clicks", n)` writes a named entry in the
  reactive store and `lumen::signal_get_int("clicks")` reads it back.
- `bind-text="clicks"` on the label. The label re-renders whenever the
  signal changes, so nothing sets its text by hand.
- CSS custom properties. Every color and radius lives in `:root`, so a
  theme swap touches one block.

`import "lumen.cdl";` pulls in the whole Lumen host surface, and `main()`
stays empty because a Lumen app does its work in the lifecycle handlers.

Run it:

```sh
lumenc run .
```
