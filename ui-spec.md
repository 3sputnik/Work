# 华泰智研 SkillHub UI specification

## 1. Principles

- Professional and trustworthy: use deep blue, brand blue, and high-lightness cool backgrounds.
- Clear and efficient: express hierarchy through type, spacing, and sections rather than decoration.
- Lightweight and restrained: use white surfaces, subtle borders, and minimal shadow.
- Extensible: use semantic tokens and a 4px spacing base.

## 2. Color tokens

| Token | Value | Usage |
|---|---:|---|
| `brand.primary` | `#0D59C4` | Primary actions, selected states, links, key icons |
| `brand.bright` | `#1E7CFF` | Brand gradient and highlights |
| `brand.cyan` | `#00C9E5` | Brand gradient and navigation indicator |
| `text.primary` | `#000000` | Headings and primary black text |
| `text.secondary` | `#4F6183` | Body copy and descriptions |
| `text.tertiary` | `#9198A7` | Versions, metadata, weak hints |
| `border.default` | `#E1E7EB` | Cards, controls, dividers |
| `surface.default` | `#FFFFFF` | Cards, sections, control surfaces |
| `surface.card` | `#F7F9FA` | Embedded dialog cards and conversation content surfaces |
| `success` | `#44BD5A` | Success and capability checks |
| `category.research` | `#1E7CFF` | Research service |
| `category.market` | `#478FC1` | Market service |
| `category.trust` | `#A374E9` | Custody service |
| `category.enterprise` | `#00C9E5` | Enterprise service |

Use category colors at about 5% opacity for tag backgrounds. Do not create near-duplicate blues.

Preferred page background:

```css
linear-gradient(180deg, #FFFFFF 0%, #E8F2FD 11%, #F4F9FE 58%, #FFFFFF 100%)
```

## 3. Typography

Font stack: `PingFang SC, Microsoft YaHei, sans-serif`. Use the approved brand display font only for the hero wordmark.

| Style | Size / line height | Weight | Usage |
|---|---:|---:|---|
| Display | 80 / 92 | 600 | Marketing hero only |
| Heading L | 18 / 25 | 600 | Section and service-group titles |
| Heading M | 16 / 22 | 600 | Card and primary content titles |
| Body | 14 / 20 | 400 | Body copy and descriptions |
| Body strong | 14 / 20 | 500 | Navigation, filters, buttons |
| Dialog Tab | 14 / 18 | 600 | Skill-dialog Tab labels |
| Caption | 14 / 18 | 400 | Versions and metadata |
| Badge | 10 / 14 | 500 | Short temporary labels such as NEW |

Pure-black headings and primary black text must be `#000000`, never `#111827`.

## 4. Spacing, radius, border, shadow

- Spacing scale: 4, 8, 12, 16, 20, 24, 32, 40px.
- Default card radius: 0px.
- Default control radius: 0px unless the approved source establishes 4 or 8px.
- Capsule tags: 100px radius.
- Default border: 1px solid `#E1E7EB`.
- Selected navigation indicator: 3px high in brand blue or cyan.
- Cards have no default shadow. Use only subtle, functional elevation when explicitly required.

## 5. Layout

- Desktop design base: 1920px.
- Centered main content: 1200px maximum width.
- Skills listing: 3 columns with 24px gaps.
- MCP service groups: 4 compact columns inside white group surfaces.
- Web implementation: use `max-width: 1200px` and flexible outer gutters; do not reproduce absolute positioning unless working inside a design canvas.

Responsive guidance:

| Width | Layout |
|---|---|
| `>=1440px` | 1200px content; Skills 3 columns; MCP 4 columns |
| `1024–1439px` | 24px gutters; Skills 2–3 columns; MCP 3 columns |
| `768–1023px` | Skills and MCP 2 columns; collapsible or scrollable navigation |
| `<768px` | Single column; horizontally scrollable filters |

## 6. Components

### Navigation

- Dark background with light text.
- Selected item uses white text and a 3px brand indicator.
- Do not use a pill background for ordinary navigation selection.
- The Skill Hub product entry may use a blue-purple gradient capsule.

### Primary tabs

- 16/22, weight 500.
- Selected text uses `#0D59C4` and a short underline.
- Keep tab positions and dimensions stable when switching.
- For Tabs inside a Skill-detail dialog, use the exact dialog-specific states and dimensions in [dialogs.md](dialogs.md); those rules override this general pattern.

### Category filter bar

- Approximately 40px high with a deep-blue background.
- 20–24px horizontal item padding.
- Selected item uses a brighter brand-blue fill.

### Buttons

- Primary: brand-blue fill, white text and icon.
- Secondary: white fill, 1px brand-blue border, brand-blue text.
- Compact height: 30–32px; horizontal padding: 12–20px; icon gap: 4–8px.
- Use verb-led labels. Keep one primary action per hierarchy level.

### Search

- Use a static or real search control according to the target surface.
- Homepage search reference: about 820px wide and 56px high on desktop.
- Use white background, `#D5DCE5` or default border, 8px radius when introduced as a prominent search field.
- Place a 16–18px search icon on the left and use tertiary text for placeholder copy.

### Capability capsules

- White fill, 100px radius, 6px vertical and 12px horizontal padding.
- 16px success icon with `#44BD5A`; 8px icon gap.
- Text: 14/18 in `#4F6183`.

### Card 1（卡片1）

Use `卡片1` as the canonical name for this card style.

- Use a three-column desktop grid. Keep each card at a fixed `384px` width and use `24px` for both column and row gaps; the three-card grid spans `1200px`.
- Keep top-level Skill resource cards white. Use `surface.card` (`#F7F9FA`) for embedded cards and conversation content areas inside dialogs.
- Use exactly `24px` internal padding on all four sides.
- Title: 16/22, weight 600, `#000000`.
- Description: 14/20, secondary text, limited to two rendered lines. Truncate overflow with an ellipsis.
- Separate metadata and action area with a 1px divider.
- Preserve equal heights within a row.

### Card 2（卡片2）

Use `卡片2` as the canonical name for the resource card with version metadata and a footer action.

- Card: fixed `384px × 254px`, `24px` padding on all sides, white fill, `1px solid #E1E7EB` border, zero radius, and no shadow.
- Grid: three cards per desktop row; use `24px` for both column and row gaps. Three cards span the `1200px` content width.
- Title: PingFang SC, `18px / 25px`, weight `600`, `#000000`.
- Version: PingFang SC, `14px / 20px`, regular, `#9198A7`; keep `16px` between title and version.
- Description block: place it `24px` below the top information row; use PingFang SC, `16px / 30px`, regular, `#4F6183`, and keep its visible area to two lines.
- Place the service label at the beginning of the description flow. Use `8px` between the label and following copy, `2px` vertical and `8px` horizontal padding, and automatic width.
- Service-label colors:
  - 托管服务: text `#A374E9`; background `rgba(163, 116, 233, 0.05)`.
  - 研究服务: text `#1E7CFF`; background `rgba(30, 124, 255, 0.05)`.
  - 行情服务: text `#478FC1`; background `rgba(71, 143, 193, 0.05)`.
  - 企业服务: text `#00C9E5`; background `rgba(0, 201, 229, 0.05)`.
- Divider: full inner width `336px`, `1px solid #E1E7EB`; keep `16px` between description and divider and `15–16px` between divider and footer controls.
- Metric text: PingFang SC, `14px / 20px`, `#9198A7`.
- Right action: `30px` high, content-driven width, `6px` vertical and `20px` horizontal padding, `1px solid #0D59C4` border, zero radius, and PingFang SC `14px / 18px` text in `#0D59C4`.
- Keep the footer aligned to the card bottom with `24px` bottom padding.

### Card 3（卡片3）

Use `卡片3` as the canonical name for the compact research-service card.

- Card: fixed `279px × 146px`, `16px` padding on all sides, white fill, `1px solid #E1E7EB` border, zero radius, and no shadow.
- Layout: vertical automatic layout with `12px` between title, description, divider, and metric row.
- Title: PingFang SC, `16px / 22px`, weight `600`, `#000000`, one line.
- Description: fixed inner width `247px`, PingFang SC `14px / 18px`, regular, `#9198A7`; limit to two lines and truncate overflow with an ellipsis.
- Divider: full inner width `247px`, `1px solid #E1E7EB`.
- Metric text: PingFang SC, `14px / 20px`, `#9198A7`, left aligned.
- Grid: four cards per row with `12px` horizontal and vertical gaps; the four-card grid spans `1152px`. Use two rows for the standard eight-card preview.

### Card 3 group header

- Section: `1200px` wide, white fill, `24px` padding; inner header and card grid width `1152px`.
- Header: `60px` high and `24px` above the card grid.
- Header title: PingFang SC, `18px / 25px`, weight `600`, `#000000`.
- Header description: PingFang SC, `16px / 22px`, regular, `#9198A7`; keep `13px` between title and description.
- Right operation button: place it at the header's right edge and vertically center it within the 60px header.
- Button: `30px` high, automatic content width with minimum width `88px`, `6px` vertical and `20px` horizontal padding, `1px solid #0D59C4` border, zero radius, white background, and PingFang SC `14px / 18px` text in `#0D59C4`.
- Keep `4px` between the button's visual symbol and text. Prevent either item from shrinking or wrapping.

### MCP service groups

- Use one white surface per service category.
- Header contains icon, 18/25 title, 14/20 description, and a right-aligned configuration action.
- Use four compact subcards per row on wide desktop.
- Use centered expand/collapse control when content exceeds the default amount.

### Card icon base plate

The inspected source set contains nine `384px × 192px` cards. This specification defines only the empty icon base plate, not the icon artwork.

- Use a fixed `60px × 60px` base plate at the card's top-left content boundary, `24px` from the card's left and top edges.
- Use `linear-gradient(180deg, #F5F7FF 0%, #EEEFFF 100%)` for the background.
- Use a `0.75px solid #E1E7EB` gray border, zero corner radius, and no shadow.
- Keep `16px` between the base plate and the title. Align the title vertically to the base plate's center.
- The base plate is a reserved placeholder only. Do not infer, generate, or document icon artwork from it.
- When no approved icon asset is provided, leave the base plate empty.

### Card category labels

- Place the category label below the card title. Keep `8px` between title text and label.
- Align the label's left edge with the title and keep the complete title/label column `16px` from the icon base plate.
- Use PingFang SC at `14px / 20px` with `2px` vertical and `8px` horizontal padding.
- Let the label hug its text; do not assign a fixed width.
- Use the following semantic colors without substitution:
  - 策略: text `#00C9E5`; background `rgba(0, 201, 229, 0.05)`.
  - 金工: text `#D86C39`; background `rgba(216, 108, 57, 0.05)`.
  - 固收: text `#478FC1`; background `rgba(71, 143, 193, 0.05)`.

## 7. Required states and accessibility

When the source defines them, include default, hover, pressed, focus, disabled, and loading states for buttons; relevant states for tabs, filters, and cards; and empty, error, unauthorized, and offline page states.

- Body-text contrast must meet 4.5:1.
- Keyboard focus must be visible.
- Icon-only actions require accessible names.
- Do not rely on color alone to communicate state.

For modal and consent states, load [dialogs.md](dialogs.md). The risk-disclosure dialog uses the approved 680px blocking-dialog pattern, scrollable legal body, checkbox acknowledgment, countdown, and disabled/enabled primary-action behavior.

## 8. Change discipline

For localized modifications, copy the existing page or component first. Change only the requested area. Preserve all unaffected copy, images, nodes, card order, dimensions, and spacing. If exact copying is impossible, say so before substituting a reconstruction.
