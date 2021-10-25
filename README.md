<div dir="rtl">

# تمرین سوم

### بند اول
ابتدا همانطور که سوال از ما خواسته است یک فایل به نام FileA.txt می‌سازیم و سپس آن را ‌commit می کنیم. در مرحله بعد می‌خواهیم یک متن به فایل موجود اضافه کنیم ولی می‌خواهیم این کار را بدون ایجاد commit جدید انجام دهیم. سپس متن را به فایل اضافه می‌کنیم.
برای اینکه بتوانیم تغییر جدید را به commit پیشین اضافه کرد باید به ترتیب مراحل زیر را اجرا کنیم:
<br>
1. 
```sh
   git add FileA.txt
```
2.
```sh
   git commit --amend --no-edit
```
در این پروژه commit دوم و سوم به اشتباه اضافه شده‌اند ولی در commit شماره ۸ این کار را به روش بالا انجام شده است.

### بند دوم
برای این بخش از سوال فایل .env را می‌سازیم و push می‌کنیم.
حال نیاز است که این فایل را به‌گونه‌ای حذف کنیم که در تاریخچه git قابل مشاهده نباشد. برای این کار مرحله زیر را انجام می‌دهیم:
1. 
```sh
   git filter-branch --force --index-filter 'git rm --cached --ignore-unmatch <path to the file or directory>' --prune-empty --tag-name-filter cat -- --all
git push origin --force --all
```
به جای path to the file or directory در اینجا dir/.env را جایگزین می‌کنیم.

### بند سوم
برای این بخش یک branch جدید ساخته شد و تغییرات بر روی این branch جدید به نام temp اضافه شد.

### بند چهارم
در این بند branch جدید ساخته شد و ۳ commit روی آن داشتیم. حال برای انکه یک commit به خصوص  از branch add-3-commit به شاخه اصلی اضافه شود ابتدا به branch main منتقل شدیم و با دستور زیر 
```
git cherry-pick f1a4d20
```
و سپس 
```
git push 
```
آن تغییر را به شاخه اصلی اضافه کردیم. شناسه f1a4d20 کد مخصوص به آن commit مورد نظر ما بود که در صفحه commit مربوط به branch مشخص است.
در مرحله آخر هم یک pull request به شاخه main میفرستیم.