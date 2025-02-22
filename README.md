# 📚 @DogPayBot 开发者文档 | Version 1.8
[![Version](https://img.shields.io/badge/version-1.8-brightgreen)](https://github.com/Mini0001/-v2board-Telegram-) [![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
---

![image](https://github.com/user-attachments/assets/de02ad48-ecd5-40c2-8cd9-19ee032513f9)  ![image](https://github.com/user-attachments/assets/a67aa4a3-9a6a-4d98-8a76-dc57b8c52a24)

---

## **💳 支付地址（重要）**  
**🚨 注意：请务必向以下官方地址发送指定金额，否则将无法完成支付。**  
**支付地址：**  
**`TN7PMwr1v17rKPTgXYb8QUdfRhTeDM62eL`**

---


## **💼 接口地址**  
`https://pay.obsdx.pw/api?key=秘钥&money=1`

---

## **📋 参数说明**  

| 参数  | 必填 | 说明                |
|-------|------|-------------------|
| key   | 是   | 你的 API 密钥      |
| money | 是   | 支付金额           |


---

## **⚙️ 请求接口说明**  
- **每3秒请求一次接口**  
  - 请求地址：`https://pay.obsdx.pw/api?key=秘钥&money=金额`  
- **接口返回内容解析：**  
  - 如果返回 `{ "success": true, "message": "Successfully" }`，表示支付已成功。  
  - 如果返回 `{ "success": false, "message": "Payment failed" }`，表示支付未成功。

---

## **🚀 详细使用说明**  

### 💵 支付金额参数说明  
- **`money=1`**：代表检查用户是否向官方地址  
  **`TN7PMwr1v17rKPTgXYb8QUdfRhTeDM62eL`** 支付了 $1 美元。  
- **`money=15.88`**：代表检查用户是否支付了 $15.88 美元。

---

### 🛠️ 处理逻辑  
1. **获取响应数据**：  
   - 向接口发起请求后，将收到一个 JSON 格式的响应。  
2. **检查 `success` 字段**：  
   - **`success: true`**  
     - 表示用户已向官方地址成功支付指定金额，可以继续处理后续业务流程（例如增加余额或发送确认通知）。  
   - **`success: false`**  
     - 表示用户未支付成功。此时可提示用户重试或稍后再检查。

---

### 🔄 请求频率建议  
- **每3秒发起一次请求**：确保不会频繁请求，避免占用过多资源，同时保证能快速检测到支付成功。  
- **持续轮询直至支付成功**：一旦收到 `success: true` 响应即可停止轮询。

---


## **⚙️ 调用示例**  
```javascript
const interval = setInterval(async () => {
  try {
    const response = await fetch('https://pay.obsdx.pw/api?key=秘钥&money=1');
    const data = await response.json();
    if (data.success) {
      console.log('支付成功!');
      clearInterval(interval);  // 支付成功后销毁定时器
    } else {
      console.log('支付失败，请稍后再试');
    }
  } catch (error) {
    console.log('请求失败，请检查网络或API');
  }
}, 3000);  // 每3秒请求一次
```
---
## **📤 返回数据**  

| 状态    | 返回数据                                         |
|---------|--------------------------------------------------|
| 成功    | `{ "success": true, "message": "Successfully" }` |
| 失败    | `{ "success": false, "message": "Payment failed" }` |

---

## ⚠️ **注意事项**

- **支付成功后，机器人将自动发送相关日志。**  
- **支付成功的金额会自动增加至狗盾钱包余额。**  
- **最终余额需在狗盾钱包中申请提现。**  
- **每次请求需间隔至少3秒，直到支付成功为止。**  
- **请确保提供正确的 API 密钥及支付金额。**

  ---

## **🔐 版权信息**  
© 2025 DogPay. All rights reserved.  
如需帮助，请联系支持团队：[@DogPayBot]([https://github.com/hanfeng888](https://t.me/DogPayBot))
