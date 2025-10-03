# حل مستوى Bandit 17
**التاريخ:** 2025-9-23  
**المصدر:** OverTheWire — Bandit

---

## 🎯 الهدف (Goal)
البحث عن كلمة السر للمستوى التالي (bandit18).  
يوجد ملفان في مجلد الـ home:
- `passwords.old`
- `passwords.new`

كلمة السر للمستوى التالي موجودة في `passwords.new` وهي السطر الوحيد المختلف بين `passwords.old` و `passwords.new`.

> ملاحظة: إذا رأيت رسالة ‘Byebye!’ عند محاولة الدخول إلى bandit18، هذا مرتبط بالمستوى التالي bandit19.

## 🔧 الأدوات المستخدمة (Tools Used)
- `ssh` - للاتصال بالخادم
- `ls` - لعرض محتويات المجلد
- `cat` - لعرض محتوى الملف
- `diff` - لمقارنة الاختلاف بين ملفين

## 🚀 طريقة الحل (Solution Steps)

1. عرض الفرق بين الملفين:
2. #diff
```bash
diff passwords.old passwords.new
```
2. النتيجة:
```diff
42c42
< CgmS55GVlEKTgx8xpW8HuWnHlBKP924b
---
> x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
```
3. تفسير النتيجة:
- `42c42` يعني أن السطر 42 مختلف بين الملفين.
- السطر الموجود بعد `>` هو السطر الجديد في `passwords.new`.

4. كلمة السر للمستوى التالي (bandit18):
```
x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
```

