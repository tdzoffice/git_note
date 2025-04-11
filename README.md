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

## နောက်ဆုံး commit 2 ခုကို ဖျက်ဖို့
``` git reset --hard HEAD~2 ``` 1ခုဆို HEAD~1
``` git push -f origin <branch-name> ``` 


To add the changes from the `develop_tdz` branch to the `master` branch, you can follow these steps:

1. **Switch to the `master` branch**:
   ```bash
   git checkout master
   ```

2. **Pull the latest changes from `master` (if there are any updates)**:
   ```bash
   git pull origin master
   ```

3. **Merge `develop_tdz` into `master`**:
   ```bash
   git merge develop_tdz
   ```

   If there are no conflicts, the merge will be successful, and the changes from `develop_tdz` will be added to `master`.

4. **Resolve any conflicts (if necessary)**:  
   If there are merge conflicts, Git will prompt you to resolve them. Open the conflicted files, fix the issues, and then stage the changes using:
   ```bash
   git add <conflicted_file>
   ```

5. **Commit the merge (if conflicts were resolved)**:
   ```bash
   git commit
   ```

   If no conflicts occurred, Git will automatically create a merge commit for you.

6. **Push the merged changes to the remote `master` branch**:
   ```bash
   git push origin master
   ```

Now, the changes from `develop_tdz` should be successfully added to `master`. Let me know if you encounter any issues!

 သုံးခုလုံး—`develop_tdz`, `develop_nhl`, တို့ကို `master` နဲ့ **forcefully** အတူတူလုပ်ချင်တယ်? ဒါဆိုတော့ လုပ်ဆောင်ရန်အဆင့်တွေကို step by step ပြောပေးမယ်နော်။

---

### ✅ Step 1: Checkout `master` branch (အရင် base branch မှာရှိဖို့လိုတယ်)

```bash
git checkout master
git pull origin master   # make sure it's up to date
```

---

### ✅ Step 2: Forcefully reset `develop_tdz` and `develop_nhl` to `master`

#### For `develop_tdz`
```bash
git checkout develop_tdz
git reset --hard master
git push origin develop_tdz --force
```

#### For `develop_nhl`
```bash
git checkout develop_nhl
git reset --hard master
git push origin develop_nhl --force
```

---

### 🧠 အရေးကြီးသော သတိပေးချက်
- `reset --hard` က local history ပြီးပြီဆိုတာပဲ ဖြစ်တယ်။  
- `--force` push လုပ်တဲ့အခါမှာ remote မှာရှိတဲ့ commits တွေ မတော်တဆ delete သွားနိုင်လို့ သတိထားပါနော်။
- သင့် project မှာ teamwork လုပ်နေတယ်ဆိုရင် teammates တွေကို အကြောင်းကြားပေးဖို့လိုပါတယ်။

---
