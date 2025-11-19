

---

# 📝 **AWS CLI S3 Upload Notes (Must Follow)**

## ✅ **1. Make sure folder path is correct**

Before uploading, always check where your folder is:

```
dir F:\
```

or

```
dir C:\Users\karan\
```

Then use the **full path** like:

```
"F:\mini_finance"
```

---

## ✅ **2. Use correct AWS CLI upload command**

Upload folder:

```
aws s3 cp "FULL_PATH_TO_FOLDER" s3://BUCKET_NAME/ --recursive --profile PROFILE_NAME
```

Example for your case:

```
aws s3 cp "F:\mini_finance" s3://minifinance-static/ --recursive --profile bhuvan
```

---

## ✅ **3. Use double quotes if path contains \ or spaces**

Always do:

✔ `"F:\folder name"`
❌ `F:\folder name`

---

## ✅ **4. Check files after upload**

```
aws s3 ls s3://BUCKET_NAME/ --recursive --profile PROFILE_NAME
```

---

## ✅ **5. S3 for website needs:**

### ✔ Public bucket policy:

```
"Effect": "Allow",
"Principal": "*",
"Action": "s3:GetObject"
```

### ✔ Block Public Access turned OFF

### ✔ Static hosting enabled

### ✔ index.html in bucket root

---

## ✅ **6. Common errors & fixes**

### ❌ **Error:** `The user-provided path does not exist`

✔ Folder path is wrong
→ Use full absolute path like `F:\mini_finance`

### ❌ **Error:** `404 NoSuchKey`

✔ index.html is not in the root of the bucket
→ Reupload correctly

### ❌ **Error:** `Access Denied`

✔ IAM user doesn’t have permissions
→ Use root or add permissions

---

## 🧠 **Always remember this simple rule:**

🔥 *AWS CLI uploads only work if the folder exists at the path you give.*

---

