# 

## လက်ရှိ Folderရဲ့ commit ကို latest commit ဖြစ်အောင်လုပ်

``` git add . ```
``` git commit --amend --no-edit ```
``` git push -f origin HEAD:master ```
"master" နေရာမှာ branch name

## .gitignore ဖိုင်တွေကို ပြန်ဖျက်ဖို့ (Update လုပ်ဖို့)
``` git clean -f -X ```
``` git rm -r --cached . ```
``` git add . ```
``` git commit -m "Update .gitignore" ```
