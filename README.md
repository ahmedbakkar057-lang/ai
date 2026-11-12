# Reckless MS API — Cloudflare Workers، ملفات في الجذر

ملفات المشروع كلها في جذر المستودع، بدون مجلدات فرعية:

```text
main.py
pyproject.toml
wrangler.jsonc
package.json
README.md
```

## حالة السجل الأخير

سجلّك الأخير يؤكد أن `npm run build` نجح. النشر وصل إلى Cloudflare، ثم توقف لأن `wrangler.jsonc` يحتوي على قيمة مؤقتة بدل معرّف KV حقيقي. كما عُدّل اسم Worker في الإعدادات إلى `ai` ليتطابق مع الاسم الذي يتوقعه ربط Cloudflare الحالي.

## إكمال الإعداد

1. من Cloudflare افتح **Storage & databases → KV → Create namespace**، وأنشئ namespace باسم `FACTS`.
2. انسخ **Namespace ID** الذي يظهر بعد الإنشاء.
3. في GitHub افتح `wrangler.jsonc`، واستبدل `REPLACE_WITH_KV_NAMESPACE_ID` بمعرّف KV الحقيقي، ثم احفظ التعديل بـCommit.
4. أضف سرًا باسم `RECKLESS_MS_API_KEY` من **Workers & Pages → ai → Settings → Variables & Secrets**.
5. أعد تشغيل النشر. اترك أمر النشر الحالي `npx wrangler deploy`؛ سجلّك يبيّن أنه وصل لمرحلة النشر بالفعل.

اربط المستودع كـ**Cloudflare Worker** وليس **Pages**. بعد نجاح النشر، استخدم رابط `workers.dev`؛ الاختبار `/health`، والوثائق `/docs`، والمحادثة `POST /chat`، وتحليل الصور `POST /image`.

للتوضيح: `name` هو اسم Worker الموجود في حسابك حاليًا (`ai`). لا تغيّره إلا إذا غيّرت اسم Worker أيضًا في إعدادات Cloudflare.
