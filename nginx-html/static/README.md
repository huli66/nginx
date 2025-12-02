# WebAssembly 中位数计算器

这是一个使用 Rust 编写的 WebAssembly 项目，提供高性能的中位数计算功能。

## 功能特性

- 支持整数和小数数组的中位数计算
- 高性能的 Rust 实现
- 可在浏览器中直接运行
- 包含完整的测试用例

## 环境要求

- Rust (1.70+)
- wasm-pack
- 现代浏览器（支持 WebAssembly）

## 安装依赖

```bash
# 安装 wasm-pack
cargo install wasm-pack
```

## 编译步骤

1. **编译 WebAssembly 模块**：
```bash
wasm-pack build --target web
```

2. **运行测试**：
```bash
cargo test
```

## 使用方法

### 在浏览器中使用

1. 编译完成后，在项目根目录启动一个本地服务器：
```bash
# 使用 Python 3
python3 -m http.server 8080

# 或使用 Node.js
npx serve .
```

2. 在浏览器中访问 `http://localhost:8080`

3. 在输入框中输入数字（用逗号分隔），点击"计算中位数"按钮

### 在 JavaScript 中使用

```javascript
import init, { calculate_median, calculate_median_int } from './pkg/test_wasm.js';

// 初始化 WebAssembly 模块
await init();

// 计算浮点数数组的中位数
const floatNumbers = [1.5, 2.5, 3.5, 4.5];
const median1 = calculate_median(floatNumbers);
console.log('浮点数中位数:', median1); // 3.0

// 计算整数数组的中位数
const intNumbers = [1, 2, 3, 4, 5];
const median2 = calculate_median_int(intNumbers);
console.log('整数中位数:', median2); // 3.0
```

## API 说明

### `calculate_median(numbers: &[f64]) -> f64`

计算浮点数数组的中位数。

**参数：**
- `numbers`: 浮点数数组

**返回值：**
- 中位数（f64 类型）

**示例：**
```rust
let numbers = vec![1.0, 2.0, 3.0, 4.0, 5.0];
let median = calculate_median(&numbers); // 返回 3.0
```

### `calculate_median_int(numbers: &[i32]) -> f64`

计算整数数组的中位数。

**参数：**
- `numbers`: 整数数组

**返回值：**
- 中位数（f64 类型）

**示例：**
```rust
let numbers = vec![1, 2, 3, 4, 5];
let median = calculate_median_int(&numbers); // 返回 3.0
```

## 算法说明

中位数计算算法：

1. 对数组进行排序
2. 如果数组长度为奇数，返回中间位置的元素
3. 如果数组长度为偶数，返回中间两个元素的平均值

**示例：**
- `[1, 2, 3, 4, 5]` → 中位数 = 3
- `[1, 2, 3, 4]` → 中位数 = (2 + 3) / 2 = 2.5

## 项目结构

```
test-wasm/
├── src/
│   └── lib.rs          # Rust 源代码
├── Cargo.toml          # Rust 项目配置
├── index.html          # 演示页面
└── README.md           # 项目说明
```

## 性能优势

- **高性能**：Rust 编译的 WebAssembly 比纯 JavaScript 实现更快
- **内存安全**：Rust 的内存安全特性确保代码的可靠性
- **跨平台**：WebAssembly 可在所有现代浏览器中运行

## 故障排除

### 常见问题

1. **编译错误**：
   - 确保已安装 `wasm-pack`
   - 检查 Rust 版本是否满足要求

2. **浏览器兼容性**：
   - 确保浏览器支持 WebAssembly
   - 使用现代浏览器（Chrome 57+, Firefox 52+, Safari 11+）

3. **模块加载失败**：
   - 确保已正确编译 WebAssembly 文件
   - 检查文件路径是否正确

## 许可证

MIT License 