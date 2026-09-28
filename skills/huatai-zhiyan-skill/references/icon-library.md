# 常用 Icon 资源库

Source: MasterGo current-file library `组件规范`, ID `local-202151150571108`.

Use this registry to replace placeholders with verified MasterGo components. Component names and variant values must match exactly.

## Local SVG archive

- Root directory: `assets/icons/16/`
- Machine-readable manifest: `assets/icons/16/manifest.json`
- The archive is grouped as `{source-order}-{component-name}/`; every SVG inside a group retains its original MasterGo asset hash for traceability.
- Prefer a verified SVG from this archive for standalone HTML. Use the manifest to resolve the component group and available exported files.
- Do not redraw, recolor, or infer missing Icon paths. If a required variant is not present in the archive, keep the placeholder or read/export that exact MasterGo variant first.

## First-batch registry

| Semantic key | Purpose | MasterGo component | Size | Supported variants |
|---|---|---|---|---|
| `download` | 下载、导出 | `16/下载` | 16×16 | 颜色：`蓝色`、`黑色`；浏览器蓝色SVG：`assets/icons/download-16-blue.svg` |
| `close` | 关闭弹窗或面板 | `16/关闭` | 16×16 | 颜色：`灰色`、`白色`、`蓝色`、`红色` |
| `close-small` | 紧凑关闭按钮 | `12/关闭` | 12×12 | 颜色：`蓝色`、`白色`、`灰色` |
| `search` | 搜索输入与搜索操作 | `16/搜索` | 16×16 | 颜色：`灰`、`白`、`蓝` |
| `copy` | 复制内容 | `16/复制` | 16×16 | 无变体 |
| `edit` | 编辑内容 | `16/编辑` | 16×16 | 无变体 |
| `delete` | 删除操作 | `16/删除` | 16×16 | 颜色：`灰`、`白`、`红`、`蓝` |
| `refresh` | 刷新、重新加载 | `16/刷新` | 16×16 | 颜色：`白`、`蓝`、`黑色` |
| `upload` | 上传文件 | `16/上传` | 16×16 | 颜色：`蓝色`、`黑色` |
| `share` | 分享 | `Icon/16/分享/蓝色` | 16×16 | 固定蓝色 |
| `info` | 提示信息 | `16/提示` | 16×16 | 无变体 |
| `success` | 成功状态 | `16/成功` | 16×16 | 颜色：`白色`、`绿色`、`蓝色` |
| `error` | 错误状态 | `16/错误` | 16×16 | 无变体 |
| `arrow` | 展开、收起、前进、返回 | `16/箭头` | 16×16 | 方向：`上`、`下`、`右`、`左`；颜色：`深灰色`、`白色`、`深蓝`、`蓝色`、`灰色`、`黑色` |

## MasterGo usage

Use the exact registered name and pass only required variant values. Examples:

```html
<ui-component name="16/下载" props='{"颜色":"蓝色"}' />
<ui-component name="16/关闭" props='{"颜色":"灰色"}' />
<ui-component name="16/箭头" props='{"方向":"下","颜色":"灰色"}' />
```

## Standalone HTML boundary

MasterGo component references do not render in a normal browser. For standalone HTML previews:

1. Use an approved local SVG from `assets/icons/16/` when one exists; consult `manifest.json` instead of scanning unrelated project assets.
2. Keep its verified 12px or 16px dimensions unless the component specification says otherwise.
3. If no approved SVG has been exported, retain the existing color-block placeholder.
4. Never reconstruct the Icon with CSS borders, pseudo-elements, emoji, or an inferred SVG path.

## Pending

- `settings/config`: the selected header contains a configuration Icon, but its exact reusable component identity has not yet been verified. Keep its placeholder until the matching component is confirmed.
- Additional common Icons can be appended in batches from the same locked MasterGo library without changing existing semantic keys.
