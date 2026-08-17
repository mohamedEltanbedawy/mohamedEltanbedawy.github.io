# tanbedawy.workbook — Portfolio

موقع بورتفوليو ستاتيك بالكامل: Vanilla HTML/CSS/JS، بدون frameworks وبدون build step. كل المسارات relative فيشتغل على GitHub Pages مباشرة أو بفتح `index.html` محليًا.

## الهيكل

```
portfolio/
├── index.html                          الصفحة الرئيسية (EN/AR بزرار تبديل)
├── case-studies/                       كل الصفحات EN/AR بنفس النظام
│   ├── commerce-os.html                Al-Raky — AI Commerce OS
│   ├── ecom-bounty.html                Affiliate Dashboard (أرقام حقيقية + الرابط الحي)
│   ├── executive-intelligence.html     كريم — منتج 1/7
│   ├── marketplace-intelligence.html   كريم — منتج 2/7
│   ├── supply-intelligence.html        كريم — منتج 3/7
│   ├── growth-intelligence.html        كريم — منتج 4/7
│   ├── pricing-intelligence.html       كريم — منتج 5/7 (نصية — بدون لقطات عمدًا)
│   ├── realtime-operations.html        كريم — منتج 6/7
│   ├── geospatial-intelligence.html    كريم — منتج 7/7
│   ├── jotia.html                      منصة Jotia (بناء هندسي مؤرشف)
│   └── egx-warehouse.html              مستودع تقييم EGX (عميل فريلانس)
├── assets/
│   ├── design-system.css               نظام التصميم المشترك (توكنز + مكوّنات)
│   └── (الصور — تُضاف لاحقًا حسب IMAGES_GUIDE.md · تظهر تلقائيًا بمجرد وضعها)
├── case-studies/automation-platform.html   منصة الأتمتة n8n
├── case-studies/salamasons.html            SalamaSons — حلقة ذكاء الإعلانات
├── IMAGES_GUIDE.md                     دليل الصور الكامل: المصدر + التمويه + الموضع
└── README.md
```

## المعاينة محليًا

افتح `index.html` في المتصفح مباشرة، أو لسيرفر محلي:

```bash
cd portfolio
python -m http.server 8000
# ثم افتح http://localhost:8000
```

## الرفع على GitHub Pages

1. أنشئ repository جديد على GitHub (مثلًا `portfolio` — أو `USERNAME.github.io` ليكون الموقع على الدومين الرئيسي).
2. من داخل فولدر `portfolio/`:

```bash
git init
git add .
git commit -m "Portfolio: unified design system, bilingual pages"
git branch -M main
git remote add origin https://github.com/USERNAME/REPO.git
git push -u origin main
```

3. في GitHub: **Settings ← Pages ← Build and deployment**
   - Source: `Deploy from a branch`
   - Branch: `main` — Folder: `/ (root)`
   - Save
4. بعد دقيقة أو اثنتين الموقع يكون على:
   - `https://USERNAME.github.io/REPO/`
   - أو `https://USERNAME.github.io/` لو الـ repo اسمه `USERNAME.github.io`

## تحديثات لاحقة

```bash
git add .
git commit -m "وصف التعديل"
git push
```

## قبل الإعلان عن الموقع — تشيك ليست

- [ ] إضافة الصور حسب `IMAGES_GUIDE.md` (مع البلور المذكور لكل صورة — **قاعدة إلزامية:** لقطات Google Sheets لا تُنشر أبدًا، ولقطات Tableau تُنشر بعد blur الأرقام المطلقة وأسماء الموردين)
- [ ] استبدال روابط `href="#"` المعلّمة بـ `<!-- TODO -->` برابط الداشبورد الحي (4 مواضع في `index.html` + 2 في `ecom-bounty.html`)
- [ ] فتح الموقع من موبايل (عرض 360px) والتأكد من النسختين EN و AR في كل الصفحات

## ملاحظات تقنية

- نظام التصميم كله في `assets/design-system.css` — أي صفحة جديدة تستورده وتلتزم بالتوكنز (`--paper`, `--ink`, `--accent`...) وأسلوب الحدود `1px solid var(--line)`.
- الخطوط من Google Fonts: Archivo (عناوين) · IBM Plex Sans / Sans Arabic (نصوص) · IBM Plex Mono (أرقام وlabels).
- `prefers-reduced-motion` محترم: أنيميشن الـ reveal يتعطل تلقائيًا.
- **الصور تلقائية:** كل مكان صورة فيه `<img>` مخفي بـ `onload/onerror` — بمجرد وضع الملف بالاسم الصحيح في `assets/` يظهر مكان الـ placeholder في كل مواضعه وفي اللغتين، بدون تعديل كود.
- تبديل اللغة client-side بالكامل (`setLang`) — نسختان كاملتان لكل صفحة مع RTL صحيح.
