# Changelog

All notable changes to the Align and Icon Panel add-ins.

The format is one entry per change, newest first. A change is not considered
done until it is pushed to `main` (which deploys via GitHub Pages) and verified
in PowerPoint. See WORKFLOW.md for the full process.

## 2026-07-28

- Align: added a "Select rounded rectangles" button to the radius section. Scans
  the current slide and selects every geometric shape with a corner adjustment,
  as a proxy for rounded rectangles (the API cannot read a shape's specific
  geometry, so this also catches other adjustable shapes and skips plain
  rectangles). Uses Slide.setSelectedShapes; needs API set 1.10 for the
  adjustment filter. Reports the count so the selection can be eyeballed before
  applying a radius.
- Align: Corner Radius UI refined per feedback. Renamed to "Rounded rectangles
  radius", dropped the subtitle and the explanatory blurb, removed the pt/mm
  toggle (points only), defaulted the field to 2 with up/down steppers, and
  added one-click presets (2, 4, 6, 8, 10 pt) that apply immediately.
- Align: added a Corner Radius section. Overrides the corner radius on selected
  rounded rectangles via the Adjustments API (index 0), non-destructively. Plain
  rectangles and other shapes are skipped by design, because the JS API cannot
  change a shape's geometry in place and recreating a shape loses attributes it
  cannot read back (shadow, glow, reflection, and more). Feature-detects
  PowerPointApi 1.10; the manifest floor was left at 1.5 so the rest of the panel
  keeps loading on older builds. Radius-to-adjustment scaling (fraction of the
  shorter side, capped at 0.5) is a best guess pending visual confirmation.
- Established the local clone and the git-based sync workflow. Added push auth
  (fine-grained token, Contents read/write, macOS Keychain). This entry is the
  end-to-end pipeline test: first commit and push from the local clone.
