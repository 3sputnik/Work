# 华泰智研 dialog specification

Source inspected: official risk-disclosure experience at `https://inst.htsc.com/skillhub?resource=1` on 2026-08-04. The selected MasterGo source set contained 10 modal-state boards, but the MCP read timed out; treat the verified official behavior below as authoritative until those boards can be read individually.

## 1. Dialog anatomy

- Full-viewport fixed overlay with `rgba(0, 0, 0, 0.40)` (`40% #000000`) mask.
- Center the dialog in the viewport.
- For content-display dialogs other than prompt dialogs, choose among `480px`, `680px`, and `880px` according to rendered content length and layout complexity.
- Start at `480px` and select the smallest approved width that presents the real content without excessive wrapping or crowding.
- Move to `680px` when 480px produces unsuitable title/body wrapping, compressed controls, or insufficient working width.
- Move to `880px` when 680px still compresses complex forms, multiple columns, dense data, comparison content, or a broader working area.
- Do not scale a content-display dialog up merely to fill space.
- Treat prompt dialogs separately: use a fixed width of `480px`, regardless of title, description, or button-label length.
- Use `680px` for risk-disclosure dialogs so they remain within the approved `480px / 680px / 880px` width system.
- Official visible modal content height: about 550px; outer modal box about 574px.
- Surface: `#FFFFFF`; no decorative shadow was observed in the inspected state.
- Header: 70px high, 24px top/bottom padding, 24px left padding, 64px right reserve.
- Body: 480px high and vertically structured as scrollable content plus a fixed footer.
- Long-form content viewport: about 382px high, horizontal padding 24px, bottom padding 24px, vertical overflow auto.
- Footer: 98px high, white surface, 1px top border `#E1E7EB`, padding 16px 24px.

## 2. Typography and color

- Dialog title: use primary black `#000000`; do not use `#111827`.
- Legal body: 14/18. The official implementation uses tertiary gray `#9198A7` for long-form disclosure text.
- Section labels and emphasized legal phrases: 14/18, weight 600.
- Consent label: 14/18 with approximately 65% black.
- Secondary action: `#4F6183` text on white.
- Primary action: `#0D59C4` background with white text.

## 3. Footer actions

- Put the acknowledgment checkbox on the first footer row.
- Put actions on the second row, right aligned.
- Keep 12px between secondary and primary actions.
- Dialog-level button height: `24px`; PingFang SC `12px / 16px`; horizontal padding `16px`; `1px` border; `0px` radius.
- Secondary action example: `暂不同意并返回`, white fill, `#E1E7EB` border.
- Primary action example: `同意并继续`, `#0D59C4` fill and border.
- Disabled primary action retains the brand fill and uses approximately 30% opacity.

### Global dialog action group

- Apply to dialog-level actions such as `取消` / `确定`, `返回` / `继续`, and equivalent secondary / primary pairs.
- Keep 40px of vertical space between the final content block and the action row.
- Keep 12px between adjacent action buttons.
- Use a fixed `24px` height and PingFang SC `12px / 16px` text for every dialog-level action.
- Measure the 40px gap from the bottom edge of the preceding visible content to the top edge of the buttons.
- If optional content above the buttons is hidden, collapse that content first, then preserve the same 40px gap from the new final visible block.
- Do not apply this 40px rule to inline, card-level, toolbar, input-suffix, or content-module buttons.

## 4. Consent state machine

```text
open
  -> countdown-running + unchecked: primary disabled
  -> countdown-complete + unchecked: primary disabled
  -> countdown-running + checked: primary disabled
  -> countdown-complete + checked: primary enabled
  -> primary action: accept and continue
  -> secondary action: decline and return
```

- Use an explicit checkbox; never infer consent from scrolling or time alone.
- A countdown may be displayed in the primary label, for example `同意并继续（5s）`.
- Enable the primary action only when the countdown is complete and the checkbox is checked.
- Keep decline available throughout the flow.
- Do not auto-check, auto-accept, or hide the decline path.

## 5. Scroll behavior

- Keep the header and footer fixed within the dialog while the legal body scrolls.
- Provide a visible scroll affordance for long content.
- Preserve the user's scroll position if only the checkbox or countdown state changes.
- Do not make reaching the bottom the only evidence of informed consent unless legal requirements explicitly demand it.

## 6. Dialog variants to document

For a complete component board, show at least:

1. Default information dialog.
2. Long-form scroll dialog.
3. Destructive confirmation dialog.
4. Risk disclosure: countdown + unchecked.
5. Risk disclosure: countdown complete + unchecked.
6. Risk disclosure: checked + countdown running.
7. Risk disclosure: checked + enabled primary action.
8. Loading/submitting state.
9. Error state with retry.
10. Success state or post-confirmation completion.

## 7. Accessibility

- Use modal semantics and move focus into the dialog on open.
- Trap keyboard focus while the blocking dialog is open.
- Return focus to the invoking control on close.
- Support Escape only when dismissal is legally and functionally permitted.
- Ensure the scrollable legal body is keyboard accessible.
- Pair disabled appearance with a programmatic disabled state.
- Do not rely on opacity or color alone; keep labels and checkbox state explicit.

## 8. Skill dialog detail introduction component

Use the fixed `Skill 弹窗详情介绍组件` directly below the dialog header. The source of truth is the selected MasterGo board `华泰skillhub-首页-tab1-弹窗1`, node `3:11687`.

### Container

- Use inside the 680px dialog with 24px left and right offsets; reference width is 632px.
- Use 16px padding and automatic height. Do not keep the reference 116px height when optional fields are hidden.
- Use `linear-gradient(110deg, rgba(13,44,196,0.05) 0%, rgba(182,222,244,0.28) 100%)`.
- Do not add a border, radius, icon, or shadow.
- Stack visible content vertically with an 8px gap.

### Optional fields

Support these independent fields. Each field may be shown or hidden:

1. `title`: optional heading.
2. `description`: optional multiline introduction.
3. `version`: optional version metadata.
4. `releaseDate`: optional release-date metadata.

When a field is hidden, remove its layer and associated gap. Never render an empty placeholder. Hide the metadata row when both `version` and `releaseDate` are absent. Keep the remaining metadata item left aligned when only one is present.

### Typography and formatting

- Title: PingFang SC, 16/22, weight 600, `#000000`.
- Description: PingFang SC, 14/20, weight 400, `#000000`.
- Metadata: PingFang SC, 12/16, weight 400, `#4F6183`.
- Join metadata labels and values without a separate gap: `版本：V1.0.1` and `发布日期：2026-06-08`.
- Use a full-width Chinese colon `：` after each metadata label.
- Format versions as uppercase `V` plus numeric segments, for example `V1.0.1`.
- Format dates as `YYYY-MM-DD`, for example `2026-06-08`.
- Keep 24px between visible metadata items.

### Composition rules

- If `title` and `description` are both visible, place the description 8px below the title.
- If metadata follows either title or description, keep an 8px vertical gap.
- If only metadata is visible, retain the 16px container padding and do not add vertical spacer layers.
- Allow the description to wrap naturally within the inner 600px reference width.

## 9. Skill dialog shell and tabs

Treat the selected MasterGo board `华泰skillhub-首页-tab1-弹窗1` as the source of truth for this Skill-dialog variant. Do not inherit shell or Tab styling from a supplied prototype.

### Dialog spacing and header

- Use a 680px dialog for this content-rich Skill-detail pattern.
- Keep content 24px from the dialog's top, right, bottom, and left edges. Apply the same 24px perimeter consistently across the header title, detail introduction, Tabs, content panels, and footer links.
- Use a white dialog surface with no decorative shadow.
- Use PingFang SC, 16/22, weight 600, `#000000` for the dialog title and secondary content titles.
- Do not add a horizontal divider, bottom border, or shadow below the dialog title/header.

### Embedded cards and conversation content

- Use `#F7F9FA` as the background color for embedded cards and conversation content surfaces inside the dialog.
- Explanatory text below Tabs uses PingFang SC, `14px / 20px`, weight `400`, and the secondary gray text color; do not bold static explanatory copy.
- Do not add a divider above the dialog input/composer area.
- Keep the close action aligned inside the same 24px top/right content boundary.
- Use a white conversation bubble with a 1px `#E1E7EB` border and no shadow.
- Use 16px horizontal padding and 20px top padding inside the conversation surface.
- Keep 24px from the bottom of the conversation bubble to the bottom edge of the `#F7F9FA` conversation surface.
- Keep a separate 24px white-space interval from the bottom of the conversation surface to the top of the input. Do not merge these two 24px intervals; the bubble-to-input distance is therefore 48px.
- Input and placeholder text use PingFang SC, `14px / 20px`, weight `400`; placeholder and weak hints use `#9198A7`.

### Skill dialog tabs

- Place the Tab row 24px below the detail-introduction component and align its left edge to the dialog's 24px content boundary.
- Use a horizontal layout with 40px between Tab items.
- Use PingFang SC, 14/18, weight 600 for every Tab label.
- Unselected state: `#000000`. Do not use secondary or tertiary gray.
- Selected state: `#0D59C4`.
- Put the selected indicator 8px below the label; use a 2px-high `#0D59C4` line matching the label width.
- Do not add a full-width baseline, container border, pill fill, or background highlight.
- Keep each Tab's width content-driven and keep all Tab positions stable when the active state changes.
- Keep 16px between the Tab row and the content panel below it.

## 10. Prompt dialogs

Use this lightweight pattern for confirmations and warnings such as irreversible actions, account switching, or status changes. Source boards: `提示弹窗1` (`3536:01672`) and `提示弹窗2` (`3536:01662`) in the MasterGo `组件规范` file.

### Container and sizing

- Use a fixed dialog width of `480px`. Do not allow the prompt-dialog container to grow or shrink with content.
- Keep long prompt copy within the 480px container through natural wrapping and automatic height. Do not switch a prompt dialog to 680px or 880px because its text is longer.
- Use automatic height. Derive the final height from the visible title, optional description, action row, and all prescribed vertical spacing.
- Use a white `#FFFFFF` surface. The inspected boards do not define a border, radius, or decorative shadow.
- Keep a 24px outer content inset.

### Icon and copy

- Use a 20px prompt icon at the top-left content boundary.
- Keep 12px between the icon and the title; the title text begins 56px from the dialog's left edge in the 480px reference layout.
- Title: PingFang SC, `16px / 22px`, weight `500`, `#000000`.
- Description is optional. When present, use PingFang SC, `14px / 18px`, weight `400`, `#4F6183`, and keep 24px below the title.
- Remove the description layer and its associated spacing when no description is shown.

### Actions and automatic layout

- Right-align the action group and keep it 24px from the dialog's right and bottom edges.
- Keep 40px between the bottom edge of the final visible text block and the top edge of the action row.
- Build each button with automatic width: let it hug the label using the approved button typography and horizontal padding. Do not copy observed button widths such as `80px`.
- Use a fixed `24px` button height and PingFang SC `12px / 16px` button text.
- Build the action group with automatic width and height. Derive its size from its child buttons and gaps; do not copy the observed `124px` group width.
- Keep 12px between two adjacent buttons. A single-button group contains no artificial second-button gap.
- Preserve the approved button component height and internal padding; do not stretch buttons merely to fill the dialog width.

### Content variants

- Title-only prompt: icon + title + action row. Reference board height was 134px, but treat this only as the result of that content and spacing, not as a fixed height.
- Title-and-description prompt: icon + title + description + action row. Reference board height was 176px, but derive future heights from content rather than fixing them to 176px.
