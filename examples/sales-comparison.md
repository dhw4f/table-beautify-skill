# 销售数据表格美化示例

## 场景

展示2024年Q4各销售员的业绩数据。

## 原始数据（未美化）

```
张三 150000 125%
李四 120000 100%
王五 90000 75%
赵六 60000 50%
```

## 美化后的Markdown表格

```markdown
## 📊 2024年Q4销售业绩表

| 销售员 | 销售额（元） | 完成率 | 排名 | 状态 |
|:------|----------:|:----:|:----:|:----:|
| 张三   | 150,000   | 125% | 🥇 1 | ✅ 超额 |
| 李四   | 120,000   | 100% | 🥈 2 | ✅ 完成 |
| 王五   |  90,000   |  75% | 🥉 3 | ⚠️ 接近 |
| 赵六   |  60,000   |  50% |   4  | ❌ 未达 |
| **合计** | **420,000** | **87.5%** | - | - |

**关键发现**：
- 🏆 **张三表现最佳**，超额完成25%，销售额15万元
- 📊 团队整体完成率87.5%，接近目标
- ⚠️ **赵六仅完成50%**，需要重点关注和辅导
- 📈 前两名差距小（3万元），后两名差距大（3万元），呈现两极分化
```

## 美化后的HTML表格

```html
<div style="max-width:800px; margin:20px auto; font-family:sans-serif;">
  <h2 style="color:#2c3e50;">📊 2024年Q4销售业绩表</h2>
  <table style="width:100%; border-collapse:collapse; box-shadow:0 2px 8px rgba(0,0,0,0.1);">
    <thead>
      <tr style="background:linear-gradient(135deg, #667eea 0%, #764ba2 100%); color:white;">
        <th style="padding:14px; text-align:left;">销售员</th>
        <th style="padding:14px; text-align:right;">销售额（元）</th>
        <th style="padding:14px; text-align:center;">完成率</th>
        <th style="padding:14px; text-align:center;">排名</th>
        <th style="padding:14px; text-align:center;">状态</th>
      </tr>
    </thead>
    <tbody>
      <tr style="border-bottom:1px solid #ecf0f1; background:#f0fff4;">
        <td style="padding:12px;"><strong>张三</strong> 🏆</td>
        <td style="padding:12px; text-align:right; color:#27ae60; font-weight:bold;">
          ¥150,000
        </td>
        <td style="padding:12px; text-align:center;">
          <div style="background:#e0e0e0; border-radius:10px; height:20px; 
                      position:relative; max-width:120px; margin:0 auto;">
            <div style="background:linear-gradient(90deg, #27ae60, #2ecc71); 
                        width:100%; height:100%; border-radius:10px;"></div>
            <span style="position:absolute; width:100%; text-align:center; 
                         top:50%; transform:translateY(-50%); font-size:11px; 
                         color:white; font-weight:bold;">
              125%
            </span>
          </div>
        </td>
        <td style="padding:12px; text-align:center; font-size:20px;">🥇</td>
        <td style="padding:12px; text-align:center;">
          <span style="background:#27ae60; color:white; padding:4px 10px; 
                       border-radius:12px; font-size:12px;">
            ✅ 超额
          </span>
        </td>
      </tr>
      <tr style="border-bottom:1px solid #ecf0f1;">
        <td style="padding:12px;">李四</td>
        <td style="padding:12px; text-align:right; font-weight:bold;">
          ¥120,000
        </td>
        <td style="padding:12px; text-align:center;">
          <div style="background:#e0e0e0; border-radius:10px; height:20px; 
                      position:relative; max-width:120px; margin:0 auto;">
            <div style="background:#3498db; width:80%; height:100%; 
                        border-radius:10px;"></div>
            <span style="position:absolute; width:100%; text-align:center; 
                         top:50%; transform:translateY(-50%); font-size:11px;">
              100%
            </span>
          </div>
        </td>
        <td style="padding:12px; text-align:center; font-size:20px;">🥈</td>
        <td style="padding:12px; text-align:center;">
          <span style="background:#3498db; color:white; padding:4px 10px; 
                       border-radius:12px; font-size:12px;">
            ✅ 完成
          </span>
        </td>
      </tr>
      <tr style="border-bottom:1px solid #ecf0f1; background:#fff8e1;">
        <td style="padding:12px;">王五</td>
        <td style="padding:12px; text-align:right;">¥90,000</td>
        <td style="padding:12px; text-align:center;">
          <div style="background:#e0e0e0; border-radius:10px; height:20px; 
                      position:relative; max-width:120px; margin:0 auto;">
            <div style="background:#f39c12; width:60%; height:100%; 
                        border-radius:10px;"></div>
            <span style="position:absolute; width:100%; text-align:center; 
                         top:50%; transform:translateY(-50%); font-size:11px;">
              75%
            </span>
          </div>
        </td>
        <td style="padding:12px; text-align:center; font-size:20px;">🥉</td>
        <td style="padding:12px; text-align:center;">
          <span style="background:#f39c12; color:white; padding:4px 10px; 
                       border-radius:12px; font-size:12px;">
            ⚠️ 接近
          </span>
        </td>
      </tr>
      <tr style="border-bottom:1px solid #ecf0f1; background:#ffebee;">
        <td style="padding:12px;">赵六</td>
        <td style="padding:12px; text-align:right; color:#e74c3c;">¥60,000</td>
        <td style="padding:12px; text-align:center;">
          <div style="background:#e0e0e0; border-radius:10px; height:20px; 
                      position:relative; max-width:120px; margin:0 auto;">
            <div style="background:#e74c3c; width:40%; height:100%; 
                        border-radius:10px;"></div>
            <span style="position:absolute; width:100%; text-align:center; 
                         top:50%; transform:translateY(-50%); font-size:11px;">
              50%
            </span>
          </div>
        </td>
        <td style="padding:12px; text-align:center; color:#95a5a6;">4</td>
        <td style="padding:12px; text-align:center;">
          <span style="background:#e74c3c; color:white; padding:4px 10px; 
                       border-radius:12px; font-size:12px;">
            ❌ 未达
          </span>
        </td>
      </tr>
      <tr style="background:#f8f9fa; font-weight:bold;">
        <td style="padding:12px;">📊 合计</td>
        <td style="padding:12px; text-align:right; color:#2c3e50;">¥420,000</td>
        <td style="padding:12px; text-align:center; color:#2c3e50;">87.5%</td>
        <td style="padding:12px; text-align:center;">-</td>
        <td style="padding:12px; text-align:center;">-</td>
      </tr>
    </tbody>
  </table>
  
  <div style="margin-top:20px; padding:15px; background:#f8f9fa; 
              border-left:4px solid #667eea; border-radius:4px;">
    <strong>💡 关键发现：</strong>
    <ul style="margin:10px 0;">
      <li>🏆 <strong>张三表现最佳</strong>，超额完成25%，销售额15万元</li>
      <li>📊 团队整体完成率87.5%，接近目标</li>
      <li>⚠️ <strong>赵六仅完成50%</strong>，需要重点关注和辅导</li>
      <li>📈 业绩呈现两极分化，前两名差距小，后两名差距大</li>
    </ul>
  </div>
</div>
```

## 美化要点解析

### 1. 数据排序
按销售额从高到低排序，一眼看到最好和最差

### 2. 极值高亮
- **最大值**（张三）：加粗 + 绿色背景 + 🏆标记
- **最小值**（赵六）：红色数字 + 红色背景 + ⚠️标记

### 3. 可视化增强
- 完成率用**进度条**展示，比纯数字更直观
- 排名用**奖牌emoji**（🥇🥈🥉）
- 状态用**彩色徽章**（✅ ⚠️ ❌）

### 4. 汇总行
底部添加合计行，便于了解整体情况

### 5. 关键发现
表格下方用文字总结洞察，帮助用户理解数据

### 6. 响应式设计
HTML版本使用相对单位，适配不同屏幕
