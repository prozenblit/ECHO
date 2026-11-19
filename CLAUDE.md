# Echo

Rebuild of the Echo KYC platform in the new Echo design system.

**For every UI task: read and follow `design-system/CLAUDE.md`** (tokens, components, rules). Use `design-system/components.md` markup and `design-system/components.css`; never invent colours, sizes, radii, icons or fonts. Anything not in the design must be derived from existing tokens and marked `EXTENDED` (CSS comment + row in the Extended table of `components.md`).

- Reference implementation: `prototypes/general-information.html` (all screens, one file). Reuse its patterns for new pages.
- Content comes from the old Echo; its old visual design must not be copied.
- Sensitive data: never copy real names, documents, account or wallet numbers. Use placeholders ({PERSON_n}, {WALLET_ADDRESS}) or clearly made-up sample data.
- Layout must hug or fill content like Figma auto layout and never overflow its container; check overflow at 1920 and 1600 px wide before saying a page is done.
- Run it by opening `prototypes/general-information.html` in a browser (no build step).
- Figma spec extracts are in `figma-spec/`.
