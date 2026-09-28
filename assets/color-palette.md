# 表格美化配色方案

## 商务专业风格

### 主色调

| 用途 | 颜色名 | 十六进制 | RGB | 预览 |
|:-----|:-------|:---------|:----|:-----|
| 主色 | 商务蓝 | `#1e3a8a` | 30, 58, 138 | 🟦 |
| 强调 | 活力橙 | `#f59e0b` | 245, 158, 11 | 🟧 |
| 成功 | 翠绿 | `#10b981` | 16, 185, 129 | 🟩 |
| 警告 | 琥珀 | `#f59e0b` | 245, 158, 11 | 🟨 |
| 危险 | 玫红 | `#ef4444` | 239, 68, 68 | 🟥 |
| 文字 | 深灰 | `#1f2937` | 31, 41, 55 | ⬛ |
| 背景 | 浅灰 | `#f9fafb` | 249, 250, 251 | ⬜ |

### CSS 变量定义

```css
:root {
  --color-primary: #1e3a8a;
  --color-accent: #f59e0b;
  --color-success: #10b981;
  --color-warning: #f59e0b;
  --color-danger: #ef4444;
  --color-text: #1f2937;
  --color-bg: #f9fafb;
  --color-border: #e5e7eb;
}
```

## 数据可视化风格

### 渐变色系

```css
/* 蓝紫渐变 - 用于表头 */
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);

/* 绿色渐变 - 用于正常/成功状态 */
background: linear-gradient(90deg, #10b981 0%, #34d399 100%);

/* 橙色渐变 - 用于警告 */
background: linear-gradient(90deg, #f59e0b 0%, #fbbf24 100%);

/* 红色渐变 - 用于危险 */
background: linear-gradient(90deg, #ef4444 0%, #f87171 100%);
```

## 状态颜色编码

### 通用状态色

| 状态 | 背景色 | 文字色 | 边框色 | Emoji |
|:-----|:-------|:-------|:-------|:------|
| 成功 | `#d1fae5` | `#065f46` | `#10b981` | ✅ |
| 警告 | `#fef3c7` | `#92400e` | `#f59e0b` | ⚠️ |
| 错误 | `#fee2e2` | `#991b1b` | `#ef4444` | ❌ |
| 信息 | `#dbeafe` | `#1e40af` | `#3b82f6` | ℹ️ |
| 进行中 | `#e0e7ff` | `#3730a3` | `#6366f1` | 🔄 |

### CSS 类定义

```css
.status-success {
  background: #d1fae5;
  color: #065f46;
  border-left: 4px solid #10b981;
  padding: 8px 12px;
}

.status-warning {
  background: #fef3c7;
  color: #92400e;
  border-left: 4px solid #f59e0b;
  padding: 8px 12px;
}

.status-danger {
  background: #fee2e2;
  color: #991b1b;
  border-left: 4px solid #ef4444;
  padding: 8px 12px;
}
```

## 数据强调色

### 极值高亮

```css
/* 最大值 - 绿色 */
.max-value {
  background: #d1fae5;
  color: #065f46;
  font-weight: bold;
}

/* 最小值 - 红色 */
.min-value {
  background: #fee2e2;
  color: #991b1b;
  font-weight: bold;
}

/* 异常值 - 黄色 */
.anomaly-value {
  background: #fef3c7;
  color: #92400e;
  font-weight: bold;
  border: 2px dashed #f59e0b;
}
```

## 进度条配色

### 标准进度条

```css
/* 0-60% 绿色 - 正常 */
.progress-normal {
  background: linear-gradient(90deg, #10b981, #34d399);
}

/* 60-85% 黄色 - 注意 */
.progress-warning {
  background: linear-gradient(90deg, #f59e0b, #fbbf24);
}

/* 85-100% 红色 - 警告 */
.progress-danger {
  background: linear-gradient(90deg, #ef4444, #f87171);
}
```

## 表格样式

### 基础表格

```css
.data-table {
  width: 100%;
  border-collapse: collapse;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
}

.data-table th {
  background: #1e3a8a;
  color: white;
  padding: 12px 16px;
  text-align: left;
  font-weight: 600;
  border-bottom: 2px solid #1e40af;
}

.data-table td {
  padding: 10px 16px;
  border-bottom: 1px solid #e5e7eb;
}

.data-table tbody tr:hover {
  background: #f9fafb;
}

.data-table tbody tr:nth-child(even) {
  background: #fafafa;
}
```

### 紧凑表格

```css
.compact-table th,
.compact-table td {
  padding: 6px 10px;
  font-size: 13px;
}
```

## 暗色主题

### 暗色配色

```css
:root[data-theme="dark"] {
  --color-bg: #1f2937;
  --color-text: #f9fafb;
  --color-border: #374151;
  --color-primary: #60a5fa;
}

.dark-table {
  background: #1f2937;
  color: #f9fafb;
}

.dark-table th {
  background: #374151;
  color: #f9fafb;
}

.dark-table td {
  border-bottom: 1px solid #374151;
}

.dark-table tbody tr:hover {
  background: #374151;
}
```

## 可访问性

### 对比度要求

WCAG 2.1 标准：
- **正常文本**：对比度 ≥ 4.5:1
- **大文本**（18pt+）：对比度 ≥ 3:1

### 推荐组合

```css
/* 高对比度组合 */
.text-on-light { color: #1f2937; background: #ffffff; }    /* 16.1:1 */
.text-on-dark { color: #ffffff; background: #1f2937; }       /* 16.1:1 */
.text-success { color: #065f46; background: #d1fae5; }      /* 7.5:1  */
.text-warning { color: #92400e; background: #fef3c7; }      /* 7.2:1  */
.text-danger { color: #991b1b; background: #fee2e2; }      /* 8.4:1  */
```

### 色盲友好

不仅依赖颜色，使用emoji和文字补充：

```html
<!-- ✓ 推荐 -->
<span class="status-success">✅ 成功</span>
<span class="status-warning">⚠️ 警告</span>
<span class="status-danger">❌ 错误</span>

<!-- ✗ 不推荐（仅依赖颜色） -->
<span style="color:green">成功</span>
<span style="color:yellow">警告</span>
<span style="color:red">错误</span>
```

## 行业配色

### 金融行业

```css
--finance-primary: #003366;  /* 深蓝 */
--finance-accent: #d4af37;   /* 金色 */
--finance-positive: #00a651; /* 涨绿 */
--finance-negative: #d32f2f; /* 跌红 */
```

### 医疗行业

```css
--medical-primary: #0066cc;  /* 医疗蓝 */
--medical-success: #28a745;  /* 健康绿 */
--medical-warning: #ffc107;  /* 警告黄 */
--medical-danger: #dc3545;   /* 危险红 */
```

### 教育行业

```css
--education-primary: #4a90e2; /* 教育蓝 */
--education-accent: #f5a623;  /* 活力橙 */
--education-success: #7ed321; /* 成长绿 */
```

### 科技行业

```css
--tech-primary: #6c5ce7;    /* 科技紫 */
--tech-accent: #00b894;     /* 创新绿 */
--tech-highlight: #fdcb6e;  /* 亮点黄 */
```
