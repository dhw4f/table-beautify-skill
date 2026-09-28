# 终端ASCII表格示例

本文件展示如何在终端/命令行环境中输出美化的ASCII表格。

## 场景1：简单数据展示

### 输出效果

```
┌──────────┬─────────┬─────────┐
│  语言    │  文件数 │ 代码行  │
├──────────┼─────────┼─────────┤
│ Python   │    45   │  12,345 │
│ JavaScript│   32   │   8,921 │
│ Go       │    18   │   4,567 │
│ Rust     │     8   │   2,103 │
├──────────┼─────────┼─────────┤
│ 合计     │   103   │  27,936 │
└──────────┴─────────┴─────────┘
```

### 生成代码（Python）

```python
def make_table(headers, rows):
    # 计算每列最大宽度
    col_widths = [len(h) for h in headers]
    for row in rows:
        for i, cell in enumerate(row):
            col_widths[i] = max(col_widths[i], len(str(cell)))

    # 生成分隔线
    sep = '+' + '+'.join('-' * (w + 2) for w in col_widths) + '+'
    top = sep.replace('-', '=')  # 顶部用双线

    # 输出表格
    print(top)
    print('| ' + ' | '.join(h.ljust(col_widths[i]) 
                              for i, h in enumerate(headers)) + ' |')
    print(sep)

    for i, row in enumerate(rows):
        print('| ' + ' | '.join(str(c).ljust(col_widths[j]) 
                                  for j, c in enumerate(row)) + ' |')
        if i < len(rows) - 1 and row == rows[-2]:  # 倒数第二行加分隔
            print(sep)

    print(sep)

# 使用示例
headers = ['语言', '文件数', '代码行']
rows = [
    ['Python', 45, '12,345'],
    ['JavaScript', 32, '8,921'],
    ['Go', 18, '4,567'],
    ['Rust', 8, '2,103'],
    ['合计', 103, '27,936'],
]
make_table(headers, rows)
```

## 场景2：带进度条的监控表格

### 输出效果

```
╔════════════════╦══════════╦════════════════════════════╗
║     指标      ║   数值   ║          进度条            ║
╠════════════════╬══════════╬════════════════════════════╣
║ CPU使用率     ║   45%    ║ ████████████░░░░░░░░ 45%   ║
║ 内存使用      ║   62%    ║ ████████████████░░░░ 62%   ║
║ 磁盘空间      ║   78%    ║ ███████████████████░ 78%   ║
║ 网络流量      ║   12%    ║ ███░░░░░░░░░░░░░░░░ 12%   ║
╚════════════════╩══════════╩════════════════════════════╝
```

### 生成代码（Python）

```python
def make_progress_bar(percentage, width=20):
    """生成进度条"""
    filled = int(width * percentage / 100)
    bar = '█' * filled + '░' * (width - filled)
    return f'{bar} {percentage}%'

def make_monitoring_table():
    metrics = [
        ('CPU使用率', 45),
        ('内存使用', 62),
        ('磁盘空间', 78),
        ('网络流量', 12),
    ]

    # 计算列宽（中文字符占2个宽度）
    def display_width(s):
        return sum(2 if ord(c) > 127 else 1 for c in str(s))

    name_width = max(display_width(m[0]) for m in metrics) + 2
    value_width = 8
    bar_width = 25

    total_width = name_width + value_width + bar_width + 7

    # 输出表格
    print('╔' + '═' * (total_width - 2) + '╗')
    print('║' + '指标'.center(name_width) + '║' + 
          '数值'.center(value_width) + '║' + 
          '进度条'.center(bar_width) + '║')
    print('╠' + '═' * (total_width - 2) + '╣')

    for name, pct in metrics:
        bar = make_progress_bar(pct, width=18)
        name_padded = ' ' * (name_width - display_width(name)) + name
        value_padded = f'{pct}%'.center(value_width)
        bar_padded = bar.center(bar_width)
        print(f'║{name_padded}║{value_padded}║{bar_padded}║')

    print('╚' + '═' * (total_width - 2) + '╝')

make_monitoring_table()
```

## 场景3：状态报告表格

### 输出效果

```
┌────────────────┬──────────┬──────────┬──────────┐
│     服务       │   状态   │  响应时间 │   CPU    │
├────────────────┼──────────┼──────────┼──────────┤
│ Web Server     │   ✓ 运行 │   45ms   │   12%    │
│ API Gateway    │   ✓ 运行 │   78ms   │   25%    │
│ Database       │   ⚠ 慢   │  234ms   │   68%    │
│ Cache          │   ✓ 运行 │    2ms   │    3%    │
│ Message Queue  │   ✗ 停止 │    N/A   │    0%    │
└────────────────┴──────────┴──────────┴──────────┘

⚠ 发现 1 个异常：Database响应时间过长
✗ 发现 1 个故障：Message Queue已停止
```

## 场景4：性能对比表格

### 输出效果

```
╔══════════════╦════════╦════════╦════════╦════════╗
║    测试项    ║  v1.0  ║  v2.0  ║  提升  ║  评级  ║
╠══════════════╬════════╬════════╬════════╬════════╣
║ 启动时间     ║ 3.2s   ║ 1.8s   ║ -44%   ║  ✓ 快  ║
║ 内存占用     ║ 256MB  ║ 128MB  ║ -50%   ║  ✓ 优  ║
║ 请求处理     ║ 1200/s ║ 2500/s ║ +108%  ║  ⭐ 佳  ║
║ 数据库查询   ║ 45ms   ║ 28ms   ║ -38%   ║  ✓ 快  ║
║ 页面加载     ║ 2.1s   ║ 1.2s   ║ -43%   ║  ✓ 快  ║
╚══════════════╩════════╩════════╩════════╩════════╝

📊 综合评分：v2.0 性能提升 56%
```

## 场景5：任务列表表格

### 输出效果

```
┌─────┬──────────────────────┬──────────┬────────┐
│ ID  │         任务         │  优先级  │  状态  │
├─────┼──────────────────────┼──────────┼────────┤
│ #1  │ 用户认证模块         │  🔴 高   │ ✅ 完成│
│ #2  │ 数据库优化           │  🟡 中   │ 🔄 进行│
│ #3  │ API文档编写          │  🟢 低   │ ⏳ 等待│
│ #4  │ 性能测试             │  🔴 高   │ ⏳ 等待│
│ #5  │ 安全审计             │  🟡 中   │ ❌ 阻塞│
└─────┴──────────────────────┴──────────┴────────┘

进度：1/5 完成 (20%)
```

## 实用工具库

### Python: tabulate

```python
from tabulate import tabulate

data = [
    ['CPU', '45%', '✓ 正常'],
    ['内存', '62%', '✓ 正常'],
    ['磁盘', '78%', '⚠ 注意'],
]

print(tabulate(data, 
               headers=['指标', '使用率', '状态'],
               tablefmt='grid'))  # grid, fancy_grid, pipe, html
```

### Python: prettytable

```python
from prettytable import PrettyTable

table = PrettyTable()
table.field_names = ['指标', '使用率', '状态']
table.add_row(['CPU', '45%', '✓ 正常'])
table.add_row(['内存', '62%', '✓ 正常'])
table.align = 'l'  # 左对齐
print(table)
```

### JavaScript: cli-table

```javascript
const Table = require('cli-table');

const table = new Table({
  head: ['指标', '使用率', '状态'],
  style: { head: ['cyan'] }
});

table.push(
  ['CPU', '45%', '✓ 正常'],
  ['内存', '62%', '✓ 正常'],
  ['磁盘', '78%', '⚠ 注意']
);

console.log(table.toString());
```

## 注意事项

### 1. 字符宽度计算

中文字符在终端中占2个字符宽度：

```python
def display_width(s):
    """计算字符串在终端中的显示宽度"""
    return sum(2 if ord(c) > 127 else 1 for c in str(s))

# "张三" -> 4
# "Zhang San" -> 8
```

### 2. Unicode 支持

确保终端支持UTF-8：
- Linux/macOS：默认支持
- Windows CMD：需要 `chcp 65001`
- Windows Terminal：默认支持

### 3. 颜色支持

使用ANSI转义序列添加颜色：

```python
# 颜色常量
RED = '\033[91m'
GREEN = '\033[92m'
YELLOW = '\033[93m'
BLUE = '\033[94m'
RESET = '\033[0m'

# 使用示例
print(f'{RED}错误{RESET} {GREEN}成功{RESET}')
```

### 4. 跨平台兼容

Windows的CMD对Unicode支持有限，建议：
- 使用基础ASCII字符（`+`, `-`, `|`, `=`）
- 避免使用emoji或复杂符号
- 或使用Windows Terminal/PowerShell
