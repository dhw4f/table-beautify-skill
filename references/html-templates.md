# HTML表格模板

## 基础美化模板

### 简洁风格

```html
<style>
.beautiful-table {
  border-collapse: collapse;
  width: 100%;
  margin: 20px 0;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
}
.beautiful-table th {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 12px;
  text-align: left;
  font-weight: 600;
}
.beautiful-table td {
  padding: 10px 12px;
  border-bottom: 1px solid #e0e0e0;
}
.beautiful-table tr:hover {
  background-color: #f5f7fa;
}
.beautiful-table .highlight {
  background-color: #fff3cd;
  font-weight: bold;
}
</style>

<table class="beautiful-table">
  <thead>
    <tr>
      <th>名称</th>
      <th style="text-align:right">数值</th>
      <th>状态</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>项目A</td>
      <td style="text-align:right">100</td>
      <td>✅ 完成</td>
    </tr>
    <tr class="highlight">
      <td><strong>项目B（重点）</strong></td>
      <td style="text-align:right"><strong>200</strong></td>
      <td>🔥 热门</td>
    </tr>
  </tbody>
</table>
```

### 商务风格

```html
<style>
.business-table {
  border-collapse: collapse;
  width: 100%;
  font-family: "Microsoft YaHei", sans-serif;
}
.business-table th {
  background-color: #2c3e50;
  color: white;
  padding: 14px;
  text-align: left;
  border-bottom: 3px solid #3498db;
}
.business-table td {
  padding: 12px 14px;
  border-bottom: 1px solid #ecf0f1;
}
.business-table tbody tr:nth-child(even) {
  background-color: #f8f9fa;
}
.business-table .max-value {
  color: #27ae60;
  font-weight: bold;
}
.business-table .min-value {
  color: #e74c3c;
  font-weight: bold;
}
</style>
```

## 数据可视化增强

### 进度条单元格

```html
<td>
  <div style="background:#e0e0e0; border-radius:4px; height:20px; position:relative;">
    <div style="background:linear-gradient(90deg, #4caf50, #8bc34a); 
                width:75%; height:100%; border-radius:4px;"></div>
    <span style="position:absolute; left:50%; top:50%; 
                 transform:translate(-50%,-50%); font-size:12px;">
      75%
    </span>
  </div>
</td>
```

### 颜色编码

```html
<!-- 正值绿色，负值红色 -->
<td style="color: #27ae60; font-weight:bold;">+15.3%</td>
<td style="color: #e74c3c; font-weight:bold;">-8.2%</td>

<!-- 状态颜色 -->
<td><span style="background:#27ae60; color:white; padding:2px 8px; 
                 border-radius:3px;">已完成</span></td>
```

### 迷你图表（Sparkline）

使用内联SVG创建迷你趋势图：

```html
<td>
  <svg width="60" height="20" viewBox="0 0 60 20">
    <polyline points="0,15 10,12 20,14 30,8 40,10 50,5 60,7" 
              fill="none" stroke="#4caf50" stroke-width="1.5"/>
  </svg>
</td>
```

## 响应式设计

### 移动端友好的滚动表格

```html
<div style="overflow-x:auto;">
  <table class="beautiful-table">
    <!-- 表格内容 -->
  </table>
</div>
```

### 移动端卡片式布局

```html
<style>
@media (max-width: 600px) {
  .responsive-table thead {
    display: none;
  }
  .responsive-table tr {
    display: block;
    margin-bottom: 10px;
    border: 1px solid #ddd;
  }
  .responsive-table td {
    display: block;
    text-align: right;
    padding-left: 50%;
    position: relative;
  }
  .responsive-table td:before {
    content: attr(data-label);
    position: absolute;
    left: 10px;
    font-weight: bold;
  }
}
</style>

<table class="responsive-table">
  <thead>
    <tr><th>名称</th><th>数值</th></tr>
  </thead>
  <tbody>
    <tr>
      <td data-label="名称">项目A</td>
      <td data-label="数值">100</td>
    </tr>
  </tbody>
</table>
```

## 完整示例：数据仪表盘表格

```html
<div style="max-width:900px; margin:20px auto; padding:20px;">
  <h2 style="color:#2c3e50;">📊 销售业绩仪表盘</h2>
  <table style="width:100%; border-collapse:collapse; font-family:sans-serif;">
    <thead>
      <tr style="background:linear-gradient(135deg, #667eea 0%, #764ba2 100%); 
                 color:white;">
        <th style="padding:14px; text-align:left;">销售员</th>
        <th style="padding:14px; text-align:right;">销售额</th>
        <th style="padding:14px; text-align:center;">完成率</th>
        <th style="padding:14px; text-align:center;">趋势</th>
        <th style="padding:14px; text-align:center;">状态</th>
      </tr>
    </thead>
    <tbody>
      <tr style="border-bottom:1px solid #ecf0f1;">
        <td style="padding:12px;">张三</td>
        <td style="padding:12px; text-align:right; font-weight:bold; color:#27ae60;">
          ¥150,000
        </td>
        <td style="padding:12px; text-align:center;">
          <div style="background:#e0e0e0; border-radius:10px; height:18px; 
                      position:relative; width:100px; margin:0 auto;">
            <div style="background:linear-gradient(90deg, #4caf50, #8bc34a); 
                        width:100%; height:100%; border-radius:10px;"></div>
            <span style="position:absolute; width:100%; text-align:center; 
                         top:50%; transform:translateY(-50%); font-size:11px;">
              125%
            </span>
          </div>
        </td>
        <td style="padding:12px; text-align:center;">
          <svg width="50" height="20" viewBox="0 0 50 20">
            <polyline points="0,15 12,10 25,12 37,5 50,7" 
                      fill="none" stroke="#4caf50" stroke-width="2"/>
          </svg>
        </td>
        <td style="padding:12px; text-align:center;">
          <span style="background:#27ae60; color:white; padding:4px 10px; 
                       border-radius:12px; font-size:12px;">
            ✅ 超额
          </span>
        </td>
      </tr>
      <!-- 更多行... -->
    </tbody>
  </table>
</div>
```

## 可访问性建议

1. **使用 `<caption>` 标签** 为表格添加标题
2. **使用 `<th scope="col/row">`** 明确表头作用范围
3. **提供文字说明** 不要只依赖颜色
4. **足够的对比度** 文字和背景对比度至少 4.5:1
5. **键盘可导航** 确保表格可以用Tab键访问
