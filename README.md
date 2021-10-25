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
