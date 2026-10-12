# ZEISS Interactive Catalogue (ZIC)

## Module reference

- **Purpose:** Staff-operated ZEISS lens consultation catalogue for Maxiview Optometrist.
- **Primary device:** 13-inch iPad Air in portrait orientation.
- **Application type:** Static single-page web application hosted with GitHub Pages.
- **Current package:** `ZIC_PRODUCT_OPTIONS_FIX_20261010_R3.zip`
- **Current release marker:** `2026-10-10-product-options-access-r3`
- **Source of truth:** The working `ZIC` GitHub repository and the latest verified full ZIP package.

This file documents the approved structure and behaviour of the current ZIC. It is not application code and does not affect the catalogue when placed in the repository.

## Purpose and consultation flow

ZIC helps staff explain, configure, compare and price ZEISS lenses during a customer consultation.

Typical flow:

1. Home
2. Select lens series
3. Select lens type
4. Select lens design
5. Configure index, coating and options
6. Review or save the build
7. Compare lenses or saved builds
8. Review the recommendation summary
9. Print the summary or label

## Product structure

| Series | Single Vision | Digital | Progressive |
| --- | --- | --- | --- |
| ZEISS Light 2 | — | Digital Light 2 3D | Light 2 D, 3D and 3DV |
| ZEISS SmartLife PRO | PRO, Individual 3 and Young PRO | Digital Lens and Digital Individual 3 | Pure, Plus, Superb and Individual 3 |
| ZEISS ClearMind PRO | Single Vision and Single Vision Individual 3 | Digital Lens and Digital Individual 3 | Pure, Plus, Superb and Individual 3 |

Individual designs are not offered under Light 2.

## Approved category-card wording

- **Single Vision:** Remains unchanged.
- **Progressive:** “Seamless vision from near to far, at every distance.”
- **Digital:** “Clear distance vision with added support for screens and close work, suitable for reading additions up to +1.25D.”

The category descriptions must remain concise and must not mention the wearer's age.

## Current comparison behaviour

### Automatic family comparison

- Selecting a lens-type family within a series immediately shows all its designs in comparison cards.
- Family display does not add lenses to the manual comparison selection.
- Each card retains its prescription information, image, starting price, ordering requirements and Compare checkbox.
- When exactly one product is displayed, its card is centred at up to 1000 px wide: name, stars, enlarged image, price and Compare on the left; benefits and ordering requirements on the right. Below 620 px it stacks vertically. Multi-product comparison cards retain their previous layout.
- Tapping an image opens the exact product menu; Back restores the same family or manual comparison and scroll position.

### General lens comparison

- Maximum of **5 lenses**.
- Comparisons stay within the selected lens type.
- Manual selections persist through Home, category menus and series switches across ClearMind, SmartLife PRO and Light 2.
- All available lens types remain visible. Changing type asks before clearing an existing manual selection; cancel preserves it.
- Clear empties the manual selection and keeps the current family comparison open.
- A series with no matching lens type opens its available category menu.
- The selected-lens bar uses short-form blue chips, such as `CMP PROG Pure`, `CMP PROG Superb` and `CMP PROG I3`.
- The old **Difference RM…** output has been removed.
- Tapping a product image or product name opens that exact lens configuration menu.
- Products without images show a clearly labelled Choose options button in place of the image; it opens the same menu. Product names and these buttons use native buttons for keyboard access.
- The menu shows **‹ Comparison** so staff can return directly to the same comparison.
- Selected lenses and comparison scroll position are preserved when returning.

### Saved-build comparison

- Up to **5 builds** can be saved during a consultation.
- **2 or 3 saved builds** can be selected for the final build comparison.
- Three builds render as three independent quotation-style cards with separate totals.
- Saved builds may come from different series and keep their own lens, index, coating, options, frame price and grand total.
- Activating a saved build restores its own frame price.
- Complimentary options use the same crossed-out price and blue **COMPLIMENTARY** pill used in the normal summary.

## Pricing and summary behaviour

- Prices are displayed in Malaysian Ringgit.
- Supported indices are product-dependent and include `1.50`, `1.60`, `1.67` and `1.74`.
- PhotoFusion X is normally a **RM500** upgrade.
- i.Scription is normally a **RM100** upgrade.
- Long-pressing an eligible option toggles its complimentary state.
- A complimentary option contributes RM0 to the total while retaining its crossed-out normal price.
- An optional frame price is included in the Grand Total.
- The single Grand Total panel and comparison Total panels use:
  - Background: `#F1F6FD`
  - Border: `#C9D9EE`
  - Active background: `#E8F1FC`
  - Dark navy price text

## Current image mappings

The three product images below use a **640 × 500 px** canvas:

| Product | Asset |
| --- | --- |
| ZEISS ClearMind PRO Digital Lens | `assets/images/cm_digital_superb.png` |
| ZEISS ClearMind PRO Digital Individual 3 | `assets/images/cm_digital_individual.png` |
| ZEISS Digital Light 2 3D | `assets/images/light2_digital.png` |

Additional approved image behaviour:

- The Light 2 Digital artwork is visually scaled to match the ClearMind images.
- ZEISS Digital Light 2 3D displays **★★**.
- The ClearMind hero artwork uses uppercase **ZEISS**.
- Current ClearMind hero asset: `assets/images/7f1bd72abbc3359f.png`.

## Features that must be preserved

- Product-specific pricing and power-range information.
- “Why this lens” information.
- Product PDFs and continuous rendered PDF pages.
- ClearMind sub-hero slide viewer.
- i.Scription interactive demonstration and information page.
- PhotoFusion X colour selection and index availability.
- Apple Pencil consultation annotations.
- Saved consultation builds.
- General lens comparison and final build comparison.
- Summary printing and Bluetooth label-print workflow.
- Complimentary option long-press behaviour.
- Direct comparison-image navigation and return-to-comparison state.

## Repository structure

```text
ZIC/
├── index.html
├── assets/
│   ├── images/
│   ├── pdfs/
│   └── pdf_pages/
├── trigger/
│   └── deploy.txt
└── ZIC_MODULE.md
```

Current verified asset counts:

- 157 image files
- 39 PDF files
- 140 rendered PDF-page images

`trigger/deploy.txt` is retained to trigger a fresh GitHub Pages deployment when required.

Do not commit any of the following:

- ZIP packages
- `.DS_Store`
- `__MACOSX`

## GitHub Pages deployment

The repository settings are:

- **Repository:** `ZIC`
- **Branch:** `main`
- **Publishing folder:** `/(root)`
- **Entry file:** lowercase `index.html`

Deployment procedure:

1. Extract the latest verified ZIC ZIP.
2. Copy `index.html`, `assets` and `trigger` into the local `ZIC` repository root.
3. Replace the existing versions when prompted.
4. Keep ZIP files, `.DS_Store` and `__MACOSX` out of the commit.
5. Review the changed files in GitHub Desktop.
6. Commit to `main`.
7. Click **Push origin**.
8. In the GitHub repository, open **Settings → Pages → Visit site**.
9. Allow up to 10 minutes for GitHub Pages to publish, then refresh the catalogue.

The normal project URL follows this pattern:

```text
https://<github-username>.github.io/ZIC/
```

## Technical notes

- The catalogue is a static client-side application; it has no customer database or server-side component.
- GitHub Pages serves it over HTTPS.
- PDF viewing uses PDF.js `3.11.174` from cdnjs and local files under `assets/pdfs` and `assets/pdf_pages`.
- All repository content hosted through GitHub Pages should be treated as public. Do not add customer or patient data.
- Bluetooth printing must be tested on the actual iPad/Bluefy workflow after changes affecting printing.

## Change-control rules

Before changing ZIC:

1. Inspect the supplied working package and confirm it is the latest deployed baseline.
2. State whether any additional files or screenshots are required.
3. Preserve every unrelated feature, price, image, PDF and interaction.
4. For requested visual changes, obtain mockup approval before coding when instructed.
5. Make the smallest necessary change.
6. Verify the final ZIP itself, not only the working folder.
7. Confirm file count and identify every changed file.
8. Test on the target iPad layout where the change affects touch, Apple Pencil, Bluetooth or portrait spacing.
9. Use a uniquely named release file when browser or download caching may cause confusion.

## Minimum release test checklist

- Home and all three series open correctly.
- Single Vision, Digital and Progressive category cards display correctly.
- Approved Digital and Progressive descriptions are present.
- Updated ClearMind and Light 2 Digital images display at the intended visual scale.
- ZEISS Digital Light 2 3D shows two stars.
- General comparison accepts five lenses and rejects a sixth.
- Saved-build comparison accepts three selected builds and rejects a fourth.
- General comparison uses short-form chips and has no Difference output.
- Comparison image opens the exact lens menu.
- **‹ Comparison** restores the same comparison and scroll position.
- Complimentary pricing does not overlap and totals correctly as RM0.
- Single and comparison Total panels use the approved pale-blue highlight.
- PhotoFusion X and i.Scription pricing and complimentary states calculate correctly.
- PDFs, ClearMind slides and the i.Scription demo open correctly.
- Summary and Bluetooth printing remain functional.
- No missing-image or missing-PDF requests appear.
- GitHub Pages loads the new release after push and hard refresh.

## September 2026 cumulative update

The current release includes:

- Uppercase ZEISS branding in the ClearMind hero.
- Corrected ClearMind Digital Lens and Digital Individual 3 images.
- Added and visually resized Light 2 Digital image.
- Two-star label for ZEISS Digital Light 2 3D.
- General comparison increased from 3 to 5 lenses.
- Saved-build comparison increased from 2 to 3 builds.
- Difference output removed.
- Short-form general-comparison chips added.
- Direct comparison-image navigation with return to Comparison.
- Corrected complimentary option styling in build comparison.
- Pale-blue Total panel treatment.
- Concise Progressive and Digital category descriptions without age references.


## October 10, 2026 release verification

Changed release files: `index.html`, `trigger/deploy.txt`, and this `ZIC_MODULE.md` (included in the ZIP). All original image, PDF and rendered-page assets remain byte-identical.

Ten automated behavioral checks passed against the packaged HTML: all families, cross-series selection through Home, comparison return navigation, cancelled/confirmed lens-type changes, Clear behavior, five-lens limit, deselect-all behavior, and three saved quotations with independent frame totals and complimentary options. Both inline scripts load successfully.

No browser automation was available in this session. Actual iPad layout, touch interactions, Apple Pencil and Bluetooth printing were not exercised. Prices and printing implementation are otherwise unchanged; saved-build comparison now includes the previously omitted frame amount.

## October 10, 2026 R2 layout update

Single-product comparison views now use the approved compact, centred two-column card. The enlarged image stage is 270 px high, or 240 px on narrow screens. Multi-product alignment spacing is not applied to a lone design. Cross-series comparison, prices, images, PDFs, saved builds and printing retain the earlier October release behavior.

The final ZIP retains 339 files. Only `index.html`, `trigger/deploy.txt` and `ZIC_MODULE.md` differ from the earlier October package. All 336 assets are byte-identical. The existing ten behavioral checks pass against the packaged HTML. Browser and actual iPad visual testing remain unavailable in this session.

## October 10, 2026 R3 options access fix

Every comparison product name now opens its exact lens options menu. The seven products without images also show a Choose options button. The prescription information icon and Compare checkbox remain separate controls. Family and manual cross-series comparison return behavior is preserved.

Twelve behavioral checks pass against the final ZIP HTML, including opening all 21 product names, opening the seven products without images, and returning from an image-free product to the same manual cross-series selection. Browser and actual iPad testing remain unavailable. The package retains 339 files and all 336 assets unchanged.
