# 设计风格指南：偏蓝红色点缀暗紫兰空间主题金融看板 (v5.0 - 游戏化UI风格)

## 一、概述

本设计指南旨在为"K次元"的Web应用提供一套统一、现代且具有游戏化UI特质的视觉和交互规范。设计灵感来源于游戏UI风格，强调深邃的暗紫兰色背景、偏蓝的红色点缀、粗边框、多层次渐变背景，以及极致简洁的图表信息展示，营造高级质感且沉浸式的用户体验。

## 二、颜色系统

### 1. 主色板 (v5.0 - 偏蓝红色点缀暗紫兰系)

```javascript
// 颜色系统 - 统一的颜色常量
// 重新设计的颜色系统，主色为偏蓝的红色，其他为低饱和度暗紫兰系

// 背景颜色
export const COLOR_BACKGROUND_DARK = '#0A0A14'; // 暗紫色背景
export const COLOR_PANEL_BACKGROUND = 'linear-gradient(170deg, #13121F 0%, #0C0B19 100%)'; // 暗紫兰渐变背景
export const COLOR_PANEL_BACKGROUND_FLAT = '#0C0B19'; // 用于klinecharts内部需要单色的地方
export const COLOR_BORDER = '#232040';         // 紫色分割线

// 主色为偏蓝的红色
export const COLOR_PRIMARY_ACTION = '#CC2029';   // 红色主色
export const COLOR_PRIMARY_ACTION_LIGHT = '#D12952'; // 主色按钮顶部亮色
export const COLOR_SECONDARY_BG = 'rgba(13, 11, 26, 0.6)'; // 次要背景色，半透明

// 辅助色系 - 低饱和度暗紫兰系
export const COLOR_ACCENT_GOLD = '#B69C58';      // 金色调整为低饱和度
export const COLOR_ACCENT_CYAN = '#3A6C86';      // 青色调整为低饱和度
export const COLOR_ACCENT_CYAN_LIGHT = '#4A7D9A'; // 用于渐变亮色
export const COLOR_ACCENT_PURPLE = '#4A3C65';   // 紫色为低饱和度
export const COLOR_TEXT_PRIMARY = '#E0E0F0';     // 主要文字
export const COLOR_TEXT_SECONDARY = '#8A889F';   // 次要文字，低饱和度
export const COLOR_TEXT_PRICE = '#B69C58';       // 价格用与低饱和度金色

// KLineChart Colors
export const KLINE_UP_COLOR = COLOR_PRIMARY_ACTION;
export const KLINE_DOWN_COLOR = COLOR_ACCENT_CYAN;
export const KLINE_GRID_COLOR = '#181830'; // K线图网格颜色调整

// 背景纹理
export const BACKGROUND_PATTERN = 'radial-gradient(rgba(70, 60, 130, 0.03) 1px, transparent 1px)';
export const BACKGROUND_PATTERN_SIZE = '30px 30px';
```

### 2. 功能色彩应用 (v5.0)

-   **背景**：
    -   页面背景：`COLOR_BACKGROUND_DARK (#0A0A14)`，搭配极低饱和度的暗紫色点状光晕
    -   组件/面板背景：不同区域使用不同方向的暗紫兰渐变，增强层次感
        - 顶部区域：`linear-gradient(90deg, rgba(25, 20, 45, 0.95) 0%, rgba(29, 24, 52, 0.85) 50%, rgba(25, 20, 45, 0.95) 100%)`
        - 用户信息区域：`linear-gradient(135deg, rgba(22, 20, 40, 0.95) 0%, rgba(18, 16, 34, 0.9) 100%)`
        - 卡片区域：`linear-gradient(165deg, rgba(20, 18, 36, 0.95) 0%, rgba(14, 12, 25, 0.9) 100%)`
        - 训练数据区域：`rgba(29, 27, 44, 0.8)`
        - 指标数据卡片：使用`rgba`半透明背景，如`rgba(189, 31, 69, 0.15)`，并搭配左侧边框
-   **外层边框**：
    -   使用纯色较粗的边框：`3px solid ${COLOR_PRIMARY_ACTION}` (移动端) / `4px solid ${COLOR_PRIMARY_ACTION}` (桌面端)
    -   外层粗边框创造游戏化UI风格，凸显界面主体
    -   内部卡片使用`1px solid ${COLOR_BORDER}`的细边框，顶部使用`3px solid ${COLOR}`的强调色
-   **文本**：
    -   主要文本/标题：`COLOR_TEXT_PRIMARY (#E0E0F0)` 或 `COLOR_ACCENT_GOLD (#B69C58)`
    -   次要信息/标签：`COLOR_TEXT_SECONDARY (#8A889F)`
    -   价格显示：`COLOR_TEXT_PRICE (#B69C58)`
-   **交互元素 (水晶/玻璃质感按钮)**：
    -   主要按钮（开始训练等）：圆角 (`borderRadius: 20px`)，背景使用偏蓝红色渐变 `linear-gradient(to bottom, ${COLOR_PRIMARY_ACTION_LIGHT}, ${COLOR_PRIMARY_ACTION})`，配合以下增强通透感的特性：
        - 内阴影：`boxShadow: inset 0 1px 2px rgba(255,255,255,0.3), inset 0 -1px 1px rgba(0,0,0,0.3)`
        - 顶部光泽层：通过绝对定位元素创建，`linear-gradient(rgb(66 0 255 / 15%), rgba(255, 255, 255, 0))`
        - 额外光效：通过绝对定位圆形元素创建，`boxShadow: 'rgb(103 1 21 / 50%) 0px -5px 10px'`
    -   次要按钮/对比按钮（如VIP按钮）：使用金色渐变 `linear-gradient(to bottom, ${COLOR_ACCENT_GOLD}, ${COLOR_ACCENT_GOLD}CC)`
    -   指标数据卡片：使用左侧边框作为颜色标识，如`borderLeft: 2px solid ${COLOR_PRIMARY_ACTION}`

### 3. 透明度与质感 (v5.0)

-   **背景网格/光晕**：`BACKGROUND_PATTERN = 'radial-gradient(rgba(70, 60, 130, 0.03) 1px, transparent 1px)'` (低饱和度暗紫色光晕)。
-   **阴影与质感**：
    -   面板阴影：`boxShadow: 0 10px 25px rgba(0,0,0,0.4)`，加深阴影营造立体感。
    -   按钮内阴影：`boxShadow: inset 0 1px 2px rgba(255,255,255,0.3), inset 0 -1px 1px rgba(0,0,0,0.3)`，强调内部光泽。
    -   顶部光泽效果：使用绝对定位元素创建顶部40%高度的渐变，模拟光源反射。
    -   卡片悬停效果：`transition-all duration-300 hover:translate-y-[-2px]`，轻微上浮效果。

## 三、布局与结构 (v5.0)

### 1. 整体布局

-   采用单页应用 (SPA) 结构，K线训练界面为核心。
-   最大内容宽度 `max-w-5xl`，居中显示。
-   移动端优先，使用响应式设计，通过 `isMobile` 状态动态调整组件尺寸。
-   使用 Tailwind CSS 的工具类进行布局，如 `flex`、`grid`、`gap` 等。

### 2. 面板与边框

-   **主容器面板**：
    -   背景：`COLOR_PANEL_BACKGROUND (linear-gradient(170deg, #13121F 0%, #0C0B19 100%))`。
    -   边框：`3px` 或 `4px` (移动端/桌面端) `solid ${COLOR_PRIMARY_ACTION}`，增强游戏化UI风格。
    -   圆角：`borderRadius: isMobile ? '18px' : '26px'`，稍增大圆角以匹配粗边框。
    -   阴影：`boxShadow: 0 10px 25px rgba(0,0,0,0.4)`，加深阴影强调立体感。
-   **内部卡片**：
    -   背景：`linear-gradient(165deg, rgba(20, 18, 36, 0.95) 0%, rgba(14, 12, 25, 0.9) 100%)`
    -   边框：`border: 1px solid ${COLOR_BORDER}`，顶部使用强调色`borderTop: 3px solid ${COLOR}`
    -   阴影：`boxShadow: 0 4px 12px rgba(0,0,0,0.2)`
    -   悬停效果：`transition-all duration-300 hover:translate-y-[-2px]`

## 四、组件规范 (v5.0)

### 1. 按钮 (Button)

-   **通用**：默认采用圆角 `borderRadius: 20px`，更圆润。
-   **主要行动按钮 (偏蓝红色水晶感)**:
    -   背景: 垂直渐变 `background: linear-gradient(to bottom, ${COLOR_PRIMARY_ACTION_LIGHT}, ${COLOR_PRIMARY_ACTION})`。
    -   文字颜色: `COLOR_TEXT_PRIMARY (#E0E0F0)`。
    -   文字阴影: `textShadow: '0 1px 2px rgba(0,0,0,0.5)'`
    -   无边框: `border: 'none'`
    -   通透水晶感实现:
      ```javascript
      {
        boxShadow: `inset 0 1px 2px rgba(255,255,255,0.3), inset 0 -1px 1px rgba(0,0,0,0.3)`,
        position: 'relative',
        overflow: 'hidden',
        backdropFilter: 'blur(5px)'
      }
      
      // 内部添加顶部光泽层
      <div style={{
        position: 'absolute',
        top: 0,
        left: 0,
        right: 0,
        height: '40%',
        background: 'linear-gradient(rgb(66 0 255 / 15%), rgba(255, 255, 255, 0))',
        borderTopLeftRadius: '20px', 
        borderTopRightRadius: '20px'
      }}></div>
      
      // 额外添加光晕效果
      <div style={{
        position: 'absolute',
        left: 0,
        top: 0,
        width: '100%',
        height: '100%',
        background: 'rgba(255,255,255,0.07)',
        borderRadius: '50%',
        transform: 'translateY(-50%)',
        boxShadow: 'rgb(103 1 21 / 50%) 0px -5px 10px'
      }}></div>
      ```
    -   尺寸: `height: isMobile ? '48px' : '50px'`，响应式调整。
-   **金色按钮 (VIP)**:
    -   背景: 垂直渐变 `background: linear-gradient(to bottom, ${COLOR_ACCENT_GOLD}, ${COLOR_ACCENT_GOLD}CC)`。
    -   文字颜色: `COLOR_TEXT_PRIMARY (#E0E0F0)`。
    -   圆角: `borderRadius: '12px'`
    -   文字阴影: `textShadow: '0 1px 1px rgba(0,0,0,0.5)'`

### 2. 数据卡片

-   **训练数据卡片**:
    -   背景: `background: rgba(29, 27, 44, 0.8)`
    -   圆角: `borderRadius: '8px'`
    -   内部指标卡片:
        - 背景: 使用对应颜色的半透明背景，如 `background: 'rgba(189, 31, 69, 0.15)'`
        - 左侧边框: `borderLeft: 2px solid ${COLOR_PRIMARY_ACTION}`
        - 圆角: `borderRadius: '6px'`
        - 内部填充: `padding: '6px 8px'`

-   **游戏化卡片**:
    -   背景: `background: linear-gradient(165deg, rgba(20, 18, 36, 0.95) 0%, rgba(14, 12, 25, 0.9) 100%)`
    -   边框: `border: 1px solid ${COLOR_BORDER}`
    -   顶部强调: `borderTop: 3px solid ${COLOR_ACCENT_GOLD/CYAN/PRIMARY_ACTION}`
    -   阴影: `boxShadow: 0 4px 12px rgba(0,0,0,0.2)`
    -   悬停效果: `transition-all duration-300 hover:translate-y-[-2px]`
    -   标题区:
        - 底部边框: `borderColor: rgba(182, 156, 88, 0.2)`
        - 渐变背景: `background: linear-gradient(to bottom, rgba(182, 156, 88, 0.1), transparent)`

### 3. 训练记录项

-   背景: `background: 'rgba(29, 27, 44, 0.5)'`
-   左侧边框: `borderLeft: 3px solid ${COLOR_ACCENT_GOLD}`
-   圆角: `rounded`
-   悬停效果: `transition-all duration-200 hover:translate-x-1`

### 4. K线图表 (klinecharts - 简洁版)

-   **核心原则：移除所有非必要的文字信息，提供纯粹的图表视觉。**
-   **背景**：由其容器决定，使用图表区渐变。
-   **网格线**：颜色 `KLINE_GRID_COLOR (#181830)`，样式 `dashed`。
-   **蜡烛图 (Candle)**:
    -   上涨颜色：`KLINE_UP_COLOR (#CC2029)` (偏蓝红色)
    -   下跌颜色：`KLINE_DOWN_COLOR (#3A6C86)` (低饱和度青色)
    -   无变化颜色：`COLOR_TEXT_SECONDARY (#8A889F)`

## 五、排版规范 (v5.0)

### 1. 字体

-   优先使用系统默认无衬线字体 (System UI, Avenir, Helvetica, Arial, sans-serif)。

### 2. 字号与行高

-   **页面标题**:
    -   移动端: `text-sm` (14px)
    -   桌面端: `text-lg` (18px)
    -   颜色: `COLOR_ACCENT_GOLD (#B69C58)`
-   **区域标签/次要信息**:
    -   移动端: `text-xs` (12px)
    -   桌面端: `text-sm` (14px)
    -   颜色: `COLOR_TEXT_SECONDARY (#8A889F)`
-   **主要数据值**:
    -   移动端: `text-sm md:text-base` (14px/16px)
    -   桌面端: `text-base md:text-lg` (16px/18px)
    -   颜色: 根据功能 (如 `COLOR_PRIMARY_ACTION`, `COLOR_ACCENT_GOLD`, `COLOR_ACCENT_CYAN`)
    -   加粗: `font-bold`
-   **超小文本**:
    -   尺寸: `text-[10px]`
    -   颜色: `COLOR_TEXT_SECONDARY (#8A889F)`

### 3. 间距

-   组件间使用 Tailwind CSS 的 `gap` 工具类 (`gap-1`, `gap-2`, `gap-3`)。
-   内边距 (`padding`): 移动端 (`px-2 py-2`, `p-3`) 和桌面端 (`px-3 py-3`, `p-4`) 有所区分。
-   外边距 (`margin`): `mb-1`, `mb-2`, `mb-4`, `mt-3`, `mt-4` 等按需使用。

## 六、响应式设计 (v5.0)

-   通过 `isMobile` 状态判断，动态调整组件尺寸、内边距、字体大小等。
-   移动端适配:
    -   边框: `3px solid ${COLOR_PRIMARY_ACTION}`
    -   圆角: `borderRadius: '18px'`
    -   布局: 使用 `flex-col` 垂直排列元素
-   桌面端适配:
    -   边框: `4px solid ${COLOR_PRIMARY_ACTION}`
    -   圆角: `borderRadius: '26px'`
    -   布局: 使用 `flex` 或 `grid` 水平排列元素

## 七、动画与过渡

-   **卡片悬停**: `transition-all duration-300 hover:translate-y-[-2px]`，轻微上浮效果。
-   **列表项悬停**: `transition-all duration-200 hover:translate-x-1`，轻微右移效果。
-   **加载状态**: 使用与主题色匹配的加载指示器 (Spin)。

## 八、设计特点与感受

-   **游戏化UI风格**：粗边框和鲜明色彩对比，创造出类似游戏界面的沉浸感。
-   **层次分明**：不同方向渐变背景区分功能区域，比内部边框更柔和、更有层次感。
-   **高对比度**：偏蓝红色 (#CC2029) 点缀在低饱和度暗紫兰环境中，创造出强烈视觉焦点。
-   **通透质感**：水晶玻璃效果按钮营造高级质感，多层次光效增强立体感。
-   **情感传达**：偏蓝红色传达出专业感和力量，与沉稳的暗紫兰背景形成平衡。
