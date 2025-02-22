# 📚 API 收款文档

## API 接口

> `https://pay.obsdx.pw/?key=秘钥&money=1`

---

## 参数说明

- **key**: 你的 API 密钥
- **money**: 支付金额（必填）

---

## 调用示例

```javascript
const interval = setInterval(async () => {
  try {
    const response = await fetch('https://pay.obsdx.pw/?key=秘钥&money=1');
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

##返回数据
成功:
{ "success": true, "message": "Successfully" }

失败:
{ "success": false, "message": "Payment failed" }


⚠️ 注意事项
✅ 支付成功后机器人会发送相关日志。
✅ 支付成功的余额自动增加到狗盾钱包余额中。
✅ 最终需要在狗盾钱包申请提现。
✅ 每次请求间隔时间为 3秒，直到支付成功为止。
❗ 请确保使用正确的 API 密钥以及支付金额。

🔐 版权信息
Dog Shield
© 2025 Dog Shield. All rights reserved.
如有任何问题，请联系支持团队：@hanfeng888
