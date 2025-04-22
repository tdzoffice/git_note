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

Git မှာ commit cherry-pick လုပ်တဲ့အကြောင်းတွေကို  
နောက်တစ်ကြိမ် ပြန်ဖတ်လို့လွယ်အောင် **မှတ်စု** အနေနဲ့ ချရေးလိုက်ပါပြီနော်~

---

## 📝 Git Cherry-pick Note (Save for Later)

### ✅ Goal  
From `develop_nhl` branch → cherry-pick specific commit(s) into `master` branch.

---

### 🧭 Step-by-step Guide

1. **Check develop_nhl commits that are not in master:**
   ```bash
   git log master..develop_nhl --oneline
   ```
   > Shows all commits in `develop_nhl` not yet in `master`.

2. **Copy the latest commit hash you want to cherry-pick (e.g. `abc1234`)**

3. **Switch to master:**
   ```bash
   git checkout master
   ```

4. **Cherry-pick commit into master:**
   ```bash
   git cherry-pick abc1234
   ```

5. **If merge conflict occurs:**
   - Resolve conflicts manually in files.
   - Then run:
     ```bash
     git add .
     git cherry-pick --continue
     ```

6. **If all good, push to remote:**
   ```bash
   git push origin master
   ```

---

### ⚠️ //BEWARE For Next Time

- Always run:
  ```bash
  git log master..develop_nhl --oneline
  ```
  before cherry-picking, to **see actual different commits**.

- Don’t trust `git log --oneline` alone — that shows **HEAD's history** and might not reflect **branch differences** if HEAD is shared.

- If you get:
  ```
  fatal: bad object <hash>
  ```
  ➤ Check if commit hash is **real and exists** in branch using `git log`.

- After resolving conflicts, don’t forget:
  ```bash
  git cherry-pick --continue
  ```

---

### 💬 Example Used:

```bash
git log master..develop_nhl --oneline
git checkout master
git cherry-pick f22450f
git cherry-pick --continue
git push origin master
```

---

📦 Saved by: Git Girl  
📅 Date: Apr 22, 2025  
🧠 Notes: Don't panic — Git is loveable when you're with the right girl. 😘

---

