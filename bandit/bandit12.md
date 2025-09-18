# حل مستوى Bandit 12
**التاريخ:** 2025-9-18 
**المصدر:** OverTheWire — Bandit  

---

## 🎯 الهدف (Goal)
> Find the password for the next level (bandit13).  
> The password is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed.

## 🔧 الأدوات المستخدمة (Tools Used)
- `ssh` - للاتصال بالخادم
- `xxd` - لتحويل hexdump إلى ملف ثنائي
- `file` - للتحقق من نوع الملف
- أدوات فك الضغط المختلفة
- 'gzip -d' - لفك ضغط ملف .gz
- 'bzip2 -d' - لفك ضغط ملف .bz2
- 'tar -xf' - لفك ضغط ملف .tar

🚀 طريقة الحل (Solution Steps)
1. الاتصال بالخادم
bash
ssh -p 2220 bandit12@bandit.labs.overthewire.org
أدخل كلمة مرور المستوى 11: 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4

2. إنشاء مجلد عمل مؤقت
cd $(mktemp -d)
cp ~/data.txt .
3. تحويل الملف من hexdump إلى ملف ثنائي
xxd -r data.txt > data.bin
rm data.txt
4. فك طبقات الضغط المتعددة
استمر في فك الضغط حتى الوصول للملف النهائي:


# الطبقة الأولى: gzip
mv data.bin data.gz
gzip -d data.gz

# الطبقة الثانية: bzip2  
mv data data.bz2
bzip2 -d data.bz2

# الطبقة الثالثة: gzip
mv data data.gz
gzip -d data.gz

# الطبقة الرابعة: tar
mv data data.tar
tar -xf data.tar
rm data.tar

# الطبقة الخامسة: tar
mv data5.bin data.tar
tar -xf data.tar
rm data.tar

# الطبقة السادسة: bzip2
mv data6.bin data.bz2
bzip2 -d data.bz2

# الطبقة السابعة: tar
mv data data.tar
tar -xf data.tar
rm data.tar

# الطبقة الثامنة: gzip
mv data8.bin data.gz
gzip -d data.gz
5. قراءة كلمة المرور
cat data
## 🔑 النتيجة (Result)
كلمة مرور المستوى 13: FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn

## 💡 ملاحظات (Notes)
- تم استخدام مجلد مؤقت (/tmp) للعمل فيه لتجنب مشاكل الصلاحيات
- المرحلة التالية: Bandit Level 13 → Level 14
- استخدمنا `file` بشكل متكرر لتحديد نوع الملف
- استخدمنا أدوات فك ضغط مختلفة حسب نوع الملف
- كل طبقة ضغط تحتاج إلى التعامل معها بالأداة المناسبة
- العملية تتطلب الصبر والتكرار حتى الوصول للملف النهائي

---
🚀 طريقة الحل التلقائية (Automated Solution)

2. تنفيذ الكود التلقائي
-------------------------------------------------------------------------------
# إنشاء مجلد مؤقت والانتقال إليه
cd $(mktemp -d)

# نسخ ملف البيانات
cp ~/data.txt .

# تحويل hexdump إلى ملف ثنائي
xxd -r data.txt > data
rm data.txt

# حلقة تلقائية لفك جميع طبقات الضغط
while true; do
    file_type=$(file data | cut -d ' ' -f 2)
    
    case "$file_type" in
        "gzip")
            mv data data.gz
            gzip -d data.gz
            ;;
        "bzip2")
            mv data data.bz2
            bzip2 -d data.bz2
            ;;
        "POSIX")
            mv data data.tar
            tar -xf data.tar
            rm data.tar
            mv data* data 2>/dev/null || true
            ;;
        "ASCII")
            # وجدنا الملف النهائي!
            break
            ;;
        *)
            echo "نوع ملف غير معروف: $(file data)"
            exit 1
            ;;
    esac
done

# عرض كلمة المرور
echo "$(cat data)"
---------------------------------------------------------------------------
