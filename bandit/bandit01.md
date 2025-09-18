# حل مستوى Bandit 1
**التاريخ:** 2025-9-12  
**المصدر:** OverTheWire — Bandit  


---

## 🎯 الهدف (Goal)
> Find the password for the next level (bandit2).  
> The password is stored in a file called - located in the home directory.

## 🔧 الأدوات المستخدمة (Tools Used)
- `ssh` - للاتصال بالخادم
- `ls` - لعرض محتويات المجلد
- `cat` - لعرض محتوى الملف

## 🚀 طريقة الحل (Solution Steps)

### 1. الاتصال بالخادم
```bash
ssh -p 2220 bandit1@bandit.labs.overthewire.org
```
أدخل كلمة مرور المستوى 0: `bandit0`

### 2. عرض الملفات
```bash
ls -la
```

### 3. قراءة الملف الذي يحمل اسم خاص
```bash
cat ./-
```

### 4. كلمة المرور المستخرجة
```
NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
```

## 💡 ملاحظات (Notes)
- اسم الملف هو `-` وهو حرف خاص في لينكس
- نستخدم `./-` للإشارة إلى الملف الحالي بدلاً من تفسيره كخيار للأمر

---