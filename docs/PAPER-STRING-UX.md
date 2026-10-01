# Paper String — UI/UX Foundation

## Product principles

Paper String is a professional creative application organized around Create → Edit → Save → Export. Artwork is the visual priority. The interface uses progressive disclosure, predictable tool behavior, restrained visual language, immediate feedback, and deliberate desktop/tablet/mobile interaction models.

## Information architecture

Home → Create Blank → Canvas Setup → Editor
Home → Browse Templates → Templates → Preview → Select → Editor
Home → Continue Project → Projects → Editor

Projects → Open / Rename / Duplicate / Delete
Templates → Browse / Search / Filter / Preview / Select
Editor → Canvas / Tools / Layers / Inspector / Pages / Undo / Redo / Save / Export
Settings → Workspace / Accessibility / Shortcuts

No public publishing, social feed, viewer mode, public profile, or paper-flip presentation exists.

## User flows

### Blank project
Create Blank → Canvas Setup → Editor → Edit → Save → Export

Canvas Setup accepts any positive width and height. Presets are shortcuts only.

### Template project
Templates → Browse → Search / Filter → Preview → Select → Editor → Customize → Save → Export

The prototype uses clearly marked development placeholders only. The final production template collection is not included.

### Existing project
Projects → Select → Open → Editor → Continue editing → Save → Export

## Editor architecture

### Desktop
Tool rail | dominant canvas stage | contextual inspector.

The editor header owns project context, undo, redo, save state, exit, and export. The page strip is persistent below the canvas.

### Tablet
The canvas remains dominant. Inspector controls may collapse to a contextual sheet or drawer while page navigation remains available. Touch targets stay comfortable.

### Mobile
The canvas is primary. Tools become a bottom bar. Inspector becomes a bottom sheet. One canvas is visible at a time. Previous/next controls and a page indicator provide immediate page switching and can be extended to swipe navigation. No theatrical page transitions.

## Canvas model

Paper String keeps these concepts distinct:

- Canvas Resize: changes workspace dimensions.
- Crop: changes the image/composition boundary.
- Image Resize: changes selected image dimensions.
- Transform: moves, scales, rotates, or flips an object.

Custom canvas dimensions are always available. Multi-canvas projects are editing surfaces, not presentation pages.

## Layer system

Conceptual layer types: Image, Text, Shape, Sticker, Drawing, and future supported objects.

Required operations: add, delete, duplicate, rename, reorder, hide/show, lock/unlock, select, merge, clip, transform, edit.

The active layer is always visible as a clear state. Tool operations target the active layer unless a feature explicitly targets another object.

## Text

Adding text creates a new text layer. Text supports content, font, size, color, opacity, position, rotation, scale, and transform. Paper String provides its own supplied fonts and may let users import fonts from a device/file picker.

## Drawing and eraser

Drawing intentionally exposes a focused brush model: size, opacity, color, responsive stroke. The eraser is active-layer based, produces transparency, and participates in the same history model as drawing.

Eraser exposes size and opacity only. Rotation is not an eraser control.

## Selection and transform

Selection defines an editing boundary. It remains until changed, cleared, or consumed by an operation.

Transform uses one consistent mental model across images, text, shapes, stickers, and future object types: move, scale, rotate, flip horizontal, flip vertical, position, and precise controls.

## Image states

Import lifecycle: idle → importing → processing/decoding → ready | unsupported | failed.

Production behavior must consider large files, transparency, EXIF orientation, slow decoding, unsupported formats, and mobile memory limits. Errors should explain recovery, not only announce failure.

## Color

A single color architecture serves drawing, text, shapes, and other editable objects: eyedropper, palette, recent colors, color history, RGB, HSV/HSB, and a full picker.

## Undo / redo

Undo and redo are primary editor controls and must participate consistently in drawing, erasing, text edits, image operations, transforms, layer changes, colors, shapes, selections, and appropriate canvas operations.

## Save states

The editor must communicate Saving, Saved, Unsaved changes, and Save failed. Autosave can be silent. Manual saving should never require an intrusive blocking flow.

## Export

Export is a primary product endpoint. The user sees the canvas/page scope and format. Output quality is automatic and high quality by default; there is no low/medium/high selector.

The renderer must preserve custom dimensions, multiple canvases, text, fonts, shapes, stickers, images, colors, transparency, and composition.

## Design system

### Typography
System-first sans stack with compact utility type. Recommended scale: 11 metadata, 12 secondary UI, 13 controls, 14 primary UI, 16 section title, 22 major subsection, 34–58 page title. Display headings are used sparingly.

### Spacing
4px base grid: 4, 8, 12, 16, 20, 24, 32, 40, 48, 64.

### Surfaces
Workspace uses warm-neutral background, white primary surfaces, subtle gray secondary surfaces, and restrained dividers. The editor uses a dark neutral canvas/stage and slightly lighter control surfaces so artwork remains visually dominant.

### Controls
Default control height: 36px. Primary actions use a solid neutral fill. Secondary actions use borders. Icon-only actions are square, labeled, and keyboard-focusable.

### Radius
Use 7–9px controls, 12–14px cards/panels, and 16–20px major surfaces. Do not round every element by default.

### Shadows
Reserve stronger shadows for transient layers and canvas separation. Use borders and surface contrast for ordinary panels.

## Component architecture

AppShell, GlobalNav, TopBar, Button, IconButton, SearchField, FilterButton, ProjectCard, TemplateCard, Modal, CanvasSetupForm, Editor, ToolRail, CanvasStage, PageStrip, Inspector, LayerList, LayerRow, RangeControl, FieldControl, SaveStatus, ExportDialog, Toast, EmptyState, SettingsNav, SettingsRow.

States: default, hover, focus, pressed, selected, disabled, loading, error, success.

## State architecture

Home: loading → empty → recent projects → recovery.
Projects: loading → empty → populated → project actions → confirmation → recovery.
Templates: loading → loaded → search/filter → no results → failed loading → preview → select → editor.
Editor: opening → ready → active selection → active tool → transform → unsaved → saving → saved → save failed → exporting → export success/failure.
Images: idle → importing → processing → ready/unsupported/failed.
Layers: no active layer → selected → hidden/locked → reordered → duplicated → renamed.

## Key interaction specifications

### Create Blank
Trigger: Create Blank.
Response: Canvas Setup modal.
Feedback: dimensions and presets are visible immediately.
Success: editor opens on the new project.

### Select Template
Trigger: Select & edit.
Response: a private project is created and editor opens.
Feedback: transition is immediate and controlled.

### Tool selection
Trigger: tool button.
Response: active tool changes.
Feedback: selected state stays visible and inspector changes to match.

### Layer selection
Trigger: layer row.
Response: active layer changes.
Feedback: layer row and inspector identify the active layer.

### Eraser
Trigger: eraser button.
Response: eraser applies to the active layer.
Feedback: size and opacity context appears; irrelevant transform controls disappear.

### Undo / redo
Trigger: toolbar button or Cmd/Ctrl+Z and Shift+Cmd/Ctrl+Z.
Response: history state changes.
Feedback: no blocking dialog; save state follows the edit history.

### Save
Trigger: autosave or Cmd/Ctrl+S.
Response: saving → saved or save failed.
Feedback: preserve the local editing state when saving fails.

### Export
Trigger: Export.
Response: compact scope/format dialog → export.
Feedback: clear queued/success/failure state.

### Mobile page switching
Trigger: previous/next, page indicator, and eventual swipe.
Response: page changes immediately.
Feedback: indicator updates; no paper-flip animation.

## Accessibility

Primary controls need semantic names, visible keyboard focus, sufficient contrast, readable text, comfortable touch targets, status messaging that is not color-only, and reduced-motion behavior. Production dialogs should manage focus and return focus to the invoking control.

## Explicit exclusions

No public sharing, public URL, viewer mode, public profile gallery, social feed, creator/viewer separation, paper-flip presentation, marketplace, fake stats, fake testimonials, generic AI dashboard panels, decorative AI gradients, or final production template library.

## Design review

For each major area ask: Is the user's task obvious? Is the primary action easy to find? Can secondary controls disappear until needed? Does the canvas remain dominant? Are important states explicit? Does keyboard behavior make sense? Does touch behavior make sense? Does mobile have its own interaction model? Does the component belong to the design system? Can anything unnecessary be removed?
