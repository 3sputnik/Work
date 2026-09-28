---
name: huatai-zhiyan-skill
description: Design, generate, modify, or review 华泰智研 SkillHub PC Web interfaces using the approved visual system and official product model. Use when Codex works on 华泰智研 or SkillHub pages, Skill and MCP listings, search and filter experiences, capability cards, installation or configuration flows, risk disclosures, design-system boards, MasterGo deliverables, or UI consistency checks for this institutional research product.
---

# 华泰智研 Skill

Apply the approved 华泰智研 UI system to every in-scope page. Read [references/ui-spec.md](references/ui-spec.md) before designing, modifying, or reviewing an interface. Read [references/product-model.md](references/product-model.md) when creating product copy, information architecture, Skill or MCP content, installation/configuration flows, API Key experiences, or compliance-related UI. Read [references/dialogs.md](references/dialogs.md) for dialogs, risk acknowledgment, blocking consent, long-form scroll content, confirmation flows, or modal state reviews.

## Workflow

1. Identify whether the request is creation, modification, or review.
2. Inspect the supplied design, prototype, screenshot, or existing implementation before changing it.
3. Preserve existing content and structure unless the user explicitly asks to change them.
4. Map all visual decisions to the tokens and component rules in the reference.
5. Reuse existing product components and assets when available.
6. For MasterGo work, follow the active MasterGo MCP tool instructions. Read the selected node before modifying it. Use page generation for new boards and targeted node updates for local changes.
7. Verify hierarchy, alignment, spacing, content preservation, state coverage, and color consistency.
8. When using the official site as a reference, treat it as the product-content source of truth and the local UI specification as the visual source of truth. Do not copy irrelevant global-site navigation into a focused SkillHub deliverable unless requested.

## Hard rules

- Use `#000000` for pure-black headings and primary black text. Do not substitute `#111827` or another near-black.
- Keep secondary and tertiary text semantic; do not convert `#4F6183` or `#9198A7` to black.
- Use the 4px spacing scale. Prefer 4, 8, 12, 16, 20, 24, 32, and 40px.
- Keep desktop content within a centered 1200px container unless an existing page establishes another value.
- Use `rgba(0, 0, 0, 0.40)` (`40% #000000`) for the standard full-screen dialog overlay.
- Use white cards with `#E1E7EB` borders and no default shadow.
- Use `#F7F9FA` for embedded dialog cards and conversation content surfaces; keep top-level resource cards white.
- Use `#0D59C4` for primary actions and selected states.
- Use PingFang SC for Chinese interface copy when the target supports it.
- Use the fixed card-icon base plate in [references/ui-spec.md](references/ui-spec.md): a 60px empty placeholder with the approved gradient background, gray border, and zero corner radius. Do not infer or generate icon artwork.
- Preserve card content, order, imagery, dimensions, and layout when the user requests a single localized change.
- Do not invent hover, disabled, loading, empty, or error treatments when the source does not define them; mark them as pending or derive them explicitly from the reference.
- Use “华泰智研” as the product name and “你的专属机构AI工具箱，一键安装，专业随行” as the official positioning copy when reproducing the current official experience.
- Keep Skill and MCP as distinct first-level resource types. Do not merge their content models.
- Do not present research data, generated summaries, forecasts, or model outputs as investment advice.
- Treat risk acknowledgment, API Key handling, authorization, and institutional-client eligibility as functional requirements rather than decorative copy.
- Keep critical consent dialogs blocking and state-driven: the primary action remains disabled until all required conditions are satisfied.

## Skill 弹窗详情介绍组件

Use the fixed `Skill 弹窗详情介绍组件` directly below a Skill dialog header. Treat the selected MasterGo board `华泰skillhub-首页-tab1-弹窗1`, node `3:11687`, as the visual source of truth. Read [references/dialogs.md](references/dialogs.md) for the exact gradient, dimensions, typography, formatting, and spacing.

- Support `title`, `description`, `version`, and `releaseDate` as independent optional fields.
- Remove a hidden field and its associated gap; never render empty placeholder layers.
- Remove the metadata row when both `version` and `releaseDate` are absent.
- Keep a single visible metadata item left aligned.
- Use automatic component height so every field combination collapses correctly.
- Format version as `版本：V1.0.1` and release date as `发布日期：YYYY-MM-DD`.
- Do not infer the component's visual styling from a prototype; use the MasterGo-derived rules in `references/dialogs.md`.

## Skill 弹窗结构与 Tab

Use the MasterGo-derived Skill dialog shell and Tab pattern in [references/dialogs.md](references/dialogs.md). These rules override the general primary-tab guidance for Skill dialogs.

- Keep 24px spacing from every dialog edge to its content.
- Do not draw a divider below the dialog title/header.
- Use PingFang SC, `16px / 22px`, weight `600`, and `#000000` for dialog titles and secondary content titles.
- Place the Tab row 24px below the detail-introduction component.
- Use PingFang SC, `14px / 18px`, weight `600` for every Skill-dialog Tab label.
- Use `#000000` for unselected Tab text; never use `#4F6183` or `#9198A7` for this state.
- Use `#0D59C4` for selected Tab text and its indicator.
- Keep Tab positions stable when switching and preserve the 40px inter-tab gap.
- Keep 16px between the Tab row and its content panel.
- Treat conversation-to-input spacing as two independent 24px spaces: 24px from the bubble to the bottom of the `#F7F9FA` conversation surface, then another 24px from that surface to the input.
- Do not draw a divider above the dialog input/composer.

## 常用弹窗宽度

Use the dialog width scale in [references/dialogs.md](references/dialogs.md) unless a verified source defines a specialized width.

- For content-display dialogs, choose among `480px`, `680px`, and `880px` according to rendered content length and layout complexity.
- Start with `480px`; move to `680px` or `880px` only when the smaller approved width creates excessive wrapping, compressed controls, or an unsuitable content layout.
- Keep prompt dialogs at a fixed width of `480px`; they do not participate in the adaptive width choice even though they share the 480px value.
- Use `680px` for risk-disclosure dialogs.

## 弹窗全局按钮组

Use this pattern for dialog-level actions such as `取消` and `确定`. Read [references/dialogs.md](references/dialogs.md) for button styling and state details.

- Keep 40px between the preceding dialog content and the global action row.
- Keep 12px between adjacent action buttons.
- Use a fixed `24px` button height and PingFang SC `12px / 16px` button text for dialog-level actions.
- Apply this spacing only to dialog-level actions, not buttons embedded inside content modules.

## 提示弹窗

Use the content-driven prompt-dialog pattern in [references/dialogs.md](references/dialogs.md) for lightweight confirmation and warning prompts.

- Use a fixed width of `480px` for prompt dialogs. Do not expand or shrink the prompt-dialog container based on copy length.
- Use automatic height based on visible title, optional description, action row, and prescribed spacing.
- Use automatic layout for every button and for the complete action group. Never hard-code observed widths such as `80px` or `124px`.
- Keep every prompt action at `24px` high with PingFang SC `12px / 16px` text.
- Let each button hug its label according to the approved button typography and internal padding; keep `12px` between two adjacent buttons.
- Keep `40px` between the final visible content and the action row, and collapse spacing for hidden optional content.

## 卡片图标底版

Read the `Card icon base plate` section in [references/ui-spec.md](references/ui-spec.md) when creating or reviewing capability cards.

- Keep the base plate at `60px × 60px`, positioned at the card's top-left content boundary.
- Use `linear-gradient(180deg, #F5F7FF 0%, #EEEFFF 100%)`, a `0.75px solid #E1E7EB` border, zero corner radius, and no shadow.
- Keep `16px` between the base plate and the card title; vertically center the title against the base plate.
- Treat the base plate as an empty reserved area. When no approved icon asset is supplied, leave it empty; do not draw, derive, or specify icon content.

## 常用 Icon 资源库

Read [references/icon-library.md](references/icon-library.md) before replacing an Icon placeholder or selecting a common operation Icon.

- In MasterGo output, use only the exact component names and supported variants recorded in the registry.
- Prefer one variant-capable base component over separate fixed-color duplicates.
- In standalone HTML, replace a placeholder only when an approved local SVG file is available. A MasterGo component name alone is not a browser-renderable asset.
- When no approved browser asset exists, keep the color-block placeholder; do not redraw or approximate the Icon.

## 卡片分类标签

Read the `Card category labels` section in [references/ui-spec.md](references/ui-spec.md) when a capability card displays a category below its title.

- Place the label `8px` below the title, align its left edge with the title, and keep the title/label column `16px` from the icon base plate.
- Use PingFang SC at `14px / 20px`; use `2px` vertical and `8px` horizontal padding so the label width follows its text.
- Use the fixed semantic pairing: 策略 `#00C9E5`, 金工 `#D86C39`, 固收 `#478FC1`.
- Set each label background to its own text color at `5%` opacity.

## 卡片1

Use the name `卡片1` for this capability-card style. Read the `Card 1（卡片1）` section in [references/ui-spec.md](references/ui-spec.md) when creating it or using it in a layout.

- Keep every card at a fixed `384px` width with `24px` padding on all four sides.
- Use three cards per desktop row. Keep both the horizontal column gap and vertical row gap at `24px`.
- Limit the gray description to two lines. When copy exceeds two rendered lines, truncate it with an ellipsis instead of increasing the visible text area.

## 卡片2

Use the name `卡片2` for the 384px resource card with version metadata, inline service label, description, divider, metric, and right-side action. Read `Card 2（卡片2）` in [references/ui-spec.md](references/ui-spec.md).

- Keep each card at `384px × 254px` with `24px` padding and a white bordered surface.
- Use three cards per desktop row with `24px` horizontal and vertical gaps.
- Preserve the verified title, version, description, service-label, divider, metric, and action hierarchy; do not replace it with Card 1 structure.
- Use the fixed service-label colors recorded in the reference.

## 卡片3与分组标题

Use the name `卡片3` for the compact research-service card. Read `Card 3（卡片3）` and `Card 3 group header` in [references/ui-spec.md](references/ui-spec.md).

- Keep each card at `279px × 146px` with `16px` padding and `12px` vertical module gaps.
- Use four cards per row with `12px` horizontal and vertical gaps; the card grid spans `1152px`.
- Use a `1200px` white section with `24px` padding when the group header is present.
- Keep the header `24px` above the card grid and place its operation button at the right edge.
- Let the operation button hug its content while preserving `20px` horizontal padding and `4px` between its visual symbol and label.

## Review output

Report concrete deviations with the affected element, observed value, required value, and recommended correction. Separate confirmed issues from suggestions.
