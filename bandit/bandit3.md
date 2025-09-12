# حل مستوى Bandit 3
**التاريخ:** 2025-9-12  
**المصدر:** OverTheWire — Bandit  


---

## 🎯 الهدف (Goal)
> Find the password for the next level (bandit4).  
> The password is stored in a hidden file in the inhere directory.

## 🔧 الأدوات المستخدمة (Tools Used)
- `ssh` - للاتصال بالخادم
- `ls` - لعرض محتويات المجلد
- `cat` - لعرض محتوى الملف

## 🚀 طريقة الحل (Solution Steps)

### 1. الاتصال بالخادم
```bash
ssh -p 2220 bandit3@bandit.labs.overthewire.org
```
أدخل كلمة مرور المستوى 2: `rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi`

### 2. الانتقال إلى المجلد
```bash
cd inhere
```

### 3. عرض الملفات المخفية
```bash
ls -la
```

### 4. قراءة الملف المخفي
```bash
cat .hidden
```

### 5. كلمة المرور المستخرجة
```
aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
```

## 💡 ملاحظات (Notes)
- الملفات التي تبدأ بنقطة (.) هي ملفات مخفية في لينكس
- نستخدم `ls -a` لعرض الملفات المخفية

---