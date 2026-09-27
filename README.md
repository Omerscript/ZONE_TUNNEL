```markdown
# ZONE TUNNEL

منصة مجانية لإنشاء أنفاق (Tunnels) تربط سكربتك المحلي بالإنترنت عبر رابط عام.

🔗 الموقع: https://omerscript.github.io/ZONE_TUNNEL/

---

## نظرة عامة

ZONE TUNNEL خدمة غير ربحية تمنحك رابطاً عاماً (URL) للوصول إلى سكربت يعمل على جهازك المحلي. لا تحتاج إلى خادم مدفوع أو إعدادات شبكة معقّدة.

---

## كيف يعمل

1. تنشئ حساباً على الموقع.
2. تنشئ مفتاح API من لوحة التحكم.
3. تضع المفتاح في سكربتك.
4. يستقبل سكربتك رابطاً عاماً تلقائياً.
5. تشارك الرابط مع من تريد.

---

## خطوات البدء

1. افتح https://omerscript.github.io/ZONE_TUNNEL/
2. أنشئ حساباً (بريد إلكتروني + كود تحقق + كلمة مرور).
3. اذهب إلى: مفاتيح API ← إنشاء مفتاح.
4. انسخ المفتاح (يبدأ بـ `zt_live_`).
5. استخدمه في سكربتك (انظر الأمثلة أدناه).

---

## ربط السكربت

### Python

```python
import requests

API_KEY  = "zt_live_xxxxxxxxxxxx"
ZONE_URL = "https://<رابط-المنصة>"
PORT     = 3000

r = requests.post(f"{ZONE_URL}/api/tunnels/register", json={
    "api_key": API_KEY,
    "local_port": PORT,
    "name": "سكربتي"
})
data = r.json()
print("رابطك:", data["tunnel"]["url"])
```

### Node.js

```javascript
const axios = require("axios");

axios.post("https://<رابط-المنصة>/api/tunnels/register", {
    api_key: "zt_live_xxxxxxxxxxxx",
    local_port: 3000,
    name: "My Script"
}).then(r => console.log("رابطك:", r.data.tunnel.url));
```

### cURL

```bash
curl -X POST "https://<رابط-المنصة>/api/tunnels/register" \
  -H "Content-Type: application/json" \
  -d '{"api_key":"zt_live_xxxx","local_port":3000,"name":"Test"}'
```

---

## نقاط API الأساسية

| المسار | الوصف |
|--------|-------|
| `POST /api/tunnels/register` | إنشاء نفق جديد |
| `POST /api/tunnels/heartbeat` | إبقاء النفق نشطاً |
| `POST /api/tunnels/disconnect` | إغلاق النفق |
| `POST /api/tunnels/list` | عرض الأنفاق |
| `POST /api/keys` | إنشاء مفتاح API |
| `POST /api/keys/list` | عرض المفاتيح |

---

## المميزات

- مجاني بالكامل وبدون إعلانات.
- بدون حد على عدد الأنفاق أو الطلبات.
- اتصال مشفّر بالكامل (TLS).
- إعداد بسيط وسريع.

---

## التواصل

- البريد الإلكتروني: zonetunnel@gmail.com
- المطوّر: @LIEI_T

---

## ملاحظة

الخدمة غير ربحية. يُمنع استخدامها في أي نشاط غير قانوني.
```
