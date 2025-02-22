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
