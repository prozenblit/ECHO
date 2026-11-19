# Parked UI (removed from the prototype, kept for later)

## Ownership: "List / Org chart" switch (removed 2026-11-17)

Where it was: `prototypes/general-information.html`, Runs screen > Ownership tab > the section head "Who owns the client", on the right of the caption. It is the existing **Tabs 24** component (`.tabs.tabs--sm`), "List" active. The Org chart view behind the second tab was never drawn, so the tab only changed its highlight.

To put it back, put this inside the `.section-head` after the `<span class="section-head__caption">Who owns the client</span>`:

```html
<div class="tabs tabs--sm" role="tablist">
  <button type="button" class="tab is-active" role="tab" aria-selected="true">List</button>
  <button type="button" class="tab" role="tab" aria-selected="false">Org chart</button>
</div>
```

The click handler that moves the highlight between tabs is already in the page script (`document.querySelectorAll('.tabs')`), so nothing else is needed. It is documented in `design-system/components.md` (Tabs and Section head).
