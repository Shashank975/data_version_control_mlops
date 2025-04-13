
# 🚀 Git + DVC Data Versioning Workflow

This project demonstrates how to manage **code using Git** and **data using DVC (Data Version Control)**. It shows how to version datasets and push them to remote storage while keeping your code and data organized and synced.

---

## 📦 Tech Stack

- 🔧 Git for code versioning  
- 📁 DVC for data versioning  
- ☁️ Simulated S3 as remote storage  

---

## 📚 Workflow Diagram

> ✅ Replace this URL with your actual diagram image hosted in the repo or an external link

![Git-DVC Workflow](https://raw.githubusercontent.com/yourusername/yourrepo/main/assets/git-dvc-workflow.png)

---

<details>
<summary>🧱 <strong>Step-by-Step Instructions</strong></summary>

### ✅ Initial Setup (V1)

1. **Clone or Initialize a Git Repo**
   ```bash
   git init
   git remote add origin <your-repo-url>
   git pull origin main
   ```

2. **Create Python Script**
   - Create `mycode.py`  
   - Add code that creates a `data/` directory and saves a CSV file into it.

3. **Initial Git Commit**
   ```bash
   git add .
   git commit -m "Initial commit with code and data"
   git push
   ```

4. **Install & Initialize DVC**
   ```bash
   pip install dvc
   dvc init
   ```

5. **Simulate Remote Directory (e.g. S3)**
   ```bash
   mkdir S3
   dvc remote add -d myremote S3
   ```

6. **Add Data Folder to DVC**
   ```bash
   dvc add data/
   git rm -r --cached data/
   git commit -m "Stop tracking data with Git"
   dvc add data/
   git add .gitignore data.dvc
   git commit -m "Track data with DVC"
   git push
   ```

7. **Push Data to DVC Remote**
   ```bash
   dvc commit
   dvc push
   git add .
   git commit -m "V1 of data"
   git push
   ```

---

### 🔁 Version 2 (V2)

8. **Update `mycode.py` to append a new row in your CSV**

9. **Track the Change**
   ```bash
   dvc status
   dvc commit
   dvc push
   git add .
   git commit -m "V2 of data"
   git push
   ```

---

### 🔁 Version 3 (V3)

10. **Again, update your CSV (simulate a new data version)**

11. **Track the New Version**
   ```bash
   dvc status
   dvc commit
   dvc push
   git add .
   git commit -m "V3 of data"
   git push
   ```

---

### ✅ Final Status Check

Make sure everything is clean and up-to-date:
```bash
dvc status
git status
```

</details>

---

## 💡 Notes & Best Practices

- 🔍 **Don’t use Git for large files** – let DVC manage your `data/` directory.
- 📌 Always commit `.dvc` files and `.gitignore` updates to Git.
- 📤 Use `dvc push` to upload data to your remote (S3, GDrive, etc.).
- 📥 Use `dvc pull` when you clone this repo elsewhere to download the data.

---

## 📁 Repo Structure (Example)

```bash
├── mycode.py
├── data/
│   └── dataset.csv
├── data.dvc
├── .gitignore
├── .dvc/
├── .dvcignore
├── S3/
└── README.md
```

---

## 🧠 Inspired by

DVC Docs: https://dvc.org/doc  
Git Docs: https://git-scm.com/doc  

---

## 🙌 Author

Built with ❤️ by [Shashank Chhoker](https://github.com/Shashank975/data_version_control_mlops)
