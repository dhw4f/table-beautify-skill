# 系统监控表格美化示例

## 场景

展示服务器各项性能指标的监控数据。

## 原始数据

```
CPU: 45%, 阈值80%, 正常
内存: 62%, 阈值85%, 正常
磁盘: 78%, 阈值90%, 注意
网络: 120MB, 阈值1GB, 正常
数据库连接: 85/100, 阈值90%, 注意
缓存命中率: 92%, 阈值80%, 正常
```

## 美化后的Markdown表格

```markdown
## 🖥️ 服务器性能监控

| 指标 | 当前值 | 阈值 | 使用率 | 状态 |
|:-----|------:|-----:|------:|:----:|
| 🔥 CPU使用率 | 45% | <80% | ████████░░░░░░░░░░ 45% | ✅ 正常 |
| 💾 内存使用 | 62% | <85% | ████████████░░░░░░░░ 62% | ✅ 正常 |
| 💿 磁盘空间 | 78% | <90% | ███████████████░░░░░ 78% | ⚠️ 注意 |
| 🌐 网络流量 | 120MB | <1GB | ██░░░░░░░░░░░░░░░░░ 12% | ✅ 正常 |
| 🗄️ 数据库连接 | 85/100 | <90 | █████████████████░░░ 85% | ⚠️ 注意 |
| ⚡ 缓存命中率 | 92% | >80% | ██████████████████░░ 92% | ✅ 优秀 |

**监控总结**：
- ✅ 整体运行正常，4项指标在安全范围
- ⚠️ **磁盘空间使用78%**，接近阈值，建议清理
- ⚠️ **数据库连接使用85%**，需要关注
- 🎯 CPU和内存使用合理，有充足余量
- 📊 系统健康评分：**82/100**
```

## 美化后的ASCII表格（适合终端）

```
╔════════════════╦═══════════╦══════════╦══════════════════════════╦══════════╗
║     指标      ║   当前值  ║   阈值   ║        可视化            ║   状态   ║
╠════════════════╬═══════════╬══════════╬══════════════════════════╬══════════╣
║ CPU使用率     ║   45%     ║   <80%   ║ ████████░░░░░░░░░░ 45%  ║  ✓ 正常  ║
║ 内存使用      ║   62%     ║   <85%   ║ ████████████░░░░░░░░ 62% ║  ✓ 正常  ║
║ 磁盘空间      ║   78%     ║   <90%   ║ ███████████████░░░░░ 78% ║  ⚠ 注意  ║
║ 网络流量      ║  120MB    ║   <1GB   ║ ██░░░░░░░░░░░░░░░░ 12%  ║  ✓ 正常  ║
║ 数据库连接    ║  85/100   ║   <90    ║ █████████████████░░░ 85% ║  ⚠ 注意  ║
║ 缓存命中率    ║   92%     ║   >80%   ║ ██████████████████░░ 92% ║  ✓ 优秀  ║
╠════════════════╬═══════════╬══════════╬══════════════════════════╬══════════╣
║ 系统健康评分  ║  82/100   ║   -      ║ ████████████████░░░░ 82% ║   良好   ║
╚════════════════╩═══════════╩══════════╩══════════════════════════╩══════════╝

💡 关键提示：
  ⚠ 磁盘空间使用 78%，建议清理
  ⚠ 数据库连接使用 85%，需要关注
  ✓ CPU 和内存使用合理
```

## 美化后的HTML表格（带颜色进度条）

```html
<div style="max-width:900px; margin:20px auto; font-family:sans-serif;">
  <div style="background:#2c3e50; color:white; padding:20px; border-radius:8px 8px 0 0;">
    <h2 style="margin:0;">🖥️ 服务器性能监控</h2>
    <p style="margin:5px 0 0 0; opacity:0.8;">实时监控 · 更新于 2024-12-19 14:30</p>
  </div>
  
  <table style="width:100%; border-collapse:collapse; box-shadow:0 2px 12px rgba(0,0,0,0.1);">
    <thead>
      <tr style="background:#34495e; color:white;">
        <th style="padding:14px; text-align:left;">指标</th>
        <th style="padding:14px; text-align:right;">当前值</th>
        <th style="padding:14px; text-align:center;">阈值</th>
        <th style="padding:14px; text-align:center; width:30%;">使用率</th>
        <th style="padding:14px; text-align:center;">状态</th>
      </tr>
    </thead>
    <tbody>
      <tr style="border-bottom:1px solid #ecf0f1;">
        <td style="padding:14px;">🔥 <strong>CPU使用率</strong></td>
        <td style="padding:14px; text-align:right; font-weight:bold; font-size:16px;">
          45%
        </td>
        <td style="padding:14px; text-align:center; color:#7f8c8d;">< 80%</td>
        <td style="padding:14px;">
          <div style="background:#ecf0f1; border-radius:10px; height:24px; position:relative;">
            <div style="background:linear-gradient(90deg, #27ae60, #2ecc71); 
                        width:45%; height:100%; border-radius:10px; 
                        transition:width 0.3s;"></div>
            <span style="position:absolute; width:100%; text-align:center; 
                         top:50%; transform:translateY(-50%); font-size:12px; 
                         font-weight:bold;">
              45%
            </span>
          </div>
        </td>
        <td style="padding:14px; text-align:center;">
          <span style="background:#27ae60; color:white; padding:4px 10px; 
                       border-radius:12px; font-size:12px;">
            ✅ 正常
          </span>
        </td>
      </tr>
      <tr style="border-bottom:1px solid #ecf0f1;">
        <td style="padding:14px;">💾 <strong>内存使用</strong></td>
        <td style="padding:14px; text-align:right; font-weight:bold; font-size:16px;">
          62%
        </td>
        <td style="padding:14px; text-align:center; color:#7f8c8d;">< 85%</td>
        <td style="padding:14px;">
          <div style="background:#ecf0f1; border-radius:10px; height:24px; position:relative;">
            <div style="background:linear-gradient(90deg, #3498db, #5dade2); 
                        width:62%; height:100%; border-radius:10px;"></div>
            <span style="position:absolute; width:100%; text-align:center; 
                         top:50%; transform:translateY(-50%); font-size:12px; 
                         font-weight:bold;">
              62%
            </span>
          </div>
        </td>
        <td style="padding:14px; text-align:center;">
          <span style="background:#27ae60; color:white; padding:4px 10px; 
                       border-radius:12px; font-size:12px;">
            ✅ 正常
          </span>
        </td>
      </tr>
      <tr style="border-bottom:1px solid #ecf0f1; background:#fff8e1;">
        <td style="padding:14px;">💿 <strong>磁盘空间</strong></td>
        <td style="padding:14px; text-align:right; font-weight:bold; font-size:16px; 
                   color:#f39c12;">
          78%
        </td>
        <td style="padding:14px; text-align:center; color:#7f8c8d;">< 90%</td>
        <td style="padding:14px;">
          <div style="background:#ecf0f1; border-radius:10px; height:24px; position:relative;">
            <div style="background:linear-gradient(90deg, #f39c12, #e67e22); 
                        width:78%; height:100%; border-radius:10px;"></div>
            <span style="position:absolute; width:100%; text-align:center; 
                         top:50%; transform:translateY(-50%); font-size:12px; 
                         font-weight:bold;">
              78%
            </span>
          </div>
        </td>
        <td style="padding:14px; text-align:center;">
          <span style="background:#f39c12; color:white; padding:4px 10px; 
                       border-radius:12px; font-size:12px;">
            ⚠️ 注意
          </span>
        </td>
      </tr>
      <tr style="border-bottom:1px solid #ecf0f1;">
        <td style="padding:14px;">🌐 <strong>网络流量</strong></td>
        <td style="padding:14px; text-align:right; font-weight:bold; font-size:16px;">
          120MB
        </td>
        <td style="padding:14px; text-align:center; color:#7f8c8d;">< 1GB</td>
        <td style="padding:14px;">
          <div style="background:#ecf0f1; border-radius:10px; height:24px; position:relative;">
            <div style="background:linear-gradient(90deg, #27ae60, #2ecc71); 
                        width:12%; height:100%; border-radius:10px;"></div>
            <span style="position:absolute; width:100%; text-align:center; 
                         top:50%; transform:translateY(-50%); font-size:12px; 
                         font-weight:bold;">
              12%
            </span>
          </div>
        </td>
        <td style="padding:14px; text-align:center;">
          <span style="background:#27ae60; color:white; padding:4px 10px; 
                       border-radius:12px; font-size:12px;">
            ✅ 正常
          </span>
        </td>
      </tr>
      <tr style="border-bottom:1px solid #ecf0f1; background:#fff8e1;">
        <td style="padding:14px;">🗄️ <strong>数据库连接</strong></td>
        <td style="padding:14px; text-align:right; font-weight:bold; font-size:16px; 
                   color:#f39c12;">
          85/100
        </td>
        <td style="padding:14px; text-align:center; color:#7f8c8d;">< 90</td>
        <td style="padding:14px;">
          <div style="background:#ecf0f1; border-radius:10px; height:24px; position:relative;">
            <div style="background:linear-gradient(90deg, #f39c12, #e67e22); 
                        width:85%; height:100%; border-radius:10px;"></div>
            <span style="position:absolute; width:100%; text-align:center; 
                         top:50%; transform:translateY(-50%); font-size:12px; 
                         font-weight:bold;">
              85%
            </span>
          </div>
        </td>
        <td style="padding:14px; text-align:center;">
          <span style="background:#f39c12; color:white; padding:4px 10px; 
                       border-radius:12px; font-size:12px;">
            ⚠️ 注意
          </span>
        </td>
      </tr>
      <tr style="border-bottom:1px solid #ecf0f1;">
        <td style="padding:14px;">⚡ <strong>缓存命中率</strong></td>
        <td style="padding:14px; text-align:right; font-weight:bold; font-size:16px; 
                   color:#27ae60;">
          92%
        </td>
        <td style="padding:14px; text-align:center; color:#7f8c8d;">> 80%</td>
        <td style="padding:14px;">
          <div style="background:#ecf0f1; border-radius:10px; height:24px; position:relative;">
            <div style="background:linear-gradient(90deg, #16a085, #1abc9c); 
                        width:92%; height:100%; border-radius:10px;"></div>
            <span style="position:absolute; width:100%; text-align:center; 
                         top:50%; transform:translateY(-50%); font-size:12px; 
                         font-weight:bold;">
              92%
            </span>
          </div>
        </td>
        <td style="padding:14px; text-align:center;">
          <span style="background:#16a085; color:white; padding:4px 10px; 
                       border-radius:12px; font-size:12px;">
            ✅ 优秀
          </span>
        </td>
      </tr>
    </tbody>
  </table>
  
  <div style="background:#f8f9fa; padding:20px; border-radius:0 0 8px 8px; 
              margin-top:-1px;">
    <h3 style="margin-top:0; color:#2c3e50;">📊 监控总结</h3>
    <div style="display:grid; grid-template-columns:repeat(2,1fr); gap:15px;">
      <div style="padding:12px; background:white; border-left:4px solid #27ae60; 
                  border-radius:4px;">
        <strong style="color:#27ae60;">✅ 正常运行 (4项)</strong>
        <p style="margin:5px 0 0 0; font-size:13px; color:#555;">
          CPU、内存、网络、缓存
        </p>
      </div>
      <div style="padding:12px; background:white; border-left:4px solid #f39c12; 
                  border-radius:4px;">
        <strong style="color:#f39c12;">⚠️ 需要注意 (2项)</strong>
        <p style="margin:5px 0 0 0; font-size:13px; color:#555;">
          磁盘空间、数据库连接
        </p>
      </div>
    </div>
    
    <div style="margin-top:15px; padding:15px; background:white; 
                border-radius:4px; text-align:center;">
      <div style="font-size:14px; color:#7f8c8d;">系统健康评分</div>
      <div style="font-size:36px; font-weight:bold; color:#27ae60; 
                  margin:5px 0;">
        82<span style="font-size:20px; color:#95a5a6;">/100</span>
      </div>
      <div style="font-size:14px; color:#27ae60;">良好</div>
    </div>
  </div>
</div>
```

## 美化要点

### 1. 可视化进度条
将百分比转换为进度条，比纯数字更直观：
- 🟢 绿色：0-60%（正常）
- 🟡 黄色：60-85%（注意）
- 🔴 红色：85-100%（警告）

### 2. 颜色编码系统
- **数值颜色**：根据数值大小显示不同颜色
- **状态徽章**：统一的颜色标识
- **行背景**：警告行用浅黄色突出

### 3. 数据排序逻辑
按风险等级排序：
- 正常 → 注意 → 警告
- 或按使用率从高到低

### 4. 汇总信息
- 顶部：标题 + 更新时间
- 底部：分类汇总 + 健康评分
- 让用户快速了解整体状况

### 5. ASCII版本特殊处理
- 终端版本使用 `█` 和 `░` 字符创建进度条
- 使用 `╔═╗` 等双线字符增强视觉效果
- 状态用符号：`✓` `⚠` `✗`

### 6. 实用性优先
- 监控表格最重要的是**快速识别异常**
- 使用颜色 + 文字双重标识，避免色盲用户无法识别
- 提供明确的行动建议（"建议清理"、"需要关注"）
