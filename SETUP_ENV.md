# Environment Setup Guide

## 1. Local Setup (Keep Secret)

**Step 1: Update `.env` file with your actual token**
- Open `.env` in your editor
- Replace `your_actual_token_here` with your real TabPFN JWT token
- Save the file
- **NEVER commit this file** (it's in `.gitignore`)

```bash
# .env file example (DO NOT COMMIT)
TABPFN_TOKEN=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyIjoiMDM2ODE5...
```

## 2. Update Your Code to Use `.env`

Add this to the top of your notebook/script:

```python
import os
from dotenv import load_dotenv

# Load environment variables from .env file
load_dotenv()

# Get token from environment
TABPFN_TOKEN = os.getenv('TABPFN_TOKEN')

if not TABPFN_TOKEN:
    raise ValueError("TABPFN_TOKEN not found in .env file!")

os.environ["TABPFN_TOKEN"] = TABPFN_TOKEN
```

**Install python-dotenv:**
```bash
pip install python-dotenv
```

## 3. GitHub Push (Safe)

```bash
# Initialize git repo (if not already done)
git init

# Add all files EXCEPT .env
git add .

# Commit
git commit -m "Initial commit"

# Add remote
git remote add origin https://github.com/tejcodess/asd-eye.git

# Push
git branch -M main
git push -u origin main
```

## 4. Verify Before Pushing

```bash
# Check what will be committed
git status

# Make sure .env is NOT listed (should say "On branch main" and "nothing to commit")
# The .env file should be shown as ignored
```

## 5. GitHub Security Check

After pushing, verify on GitHub:
1. Visit: https://github.com/tejcodess/asd-eye
2. Check that `.env` file is NOT visible
3. Only `.env.example` should be visible (without real values)

## Share with Team

- Share `.env.example` with team members
- They can copy it to `.env` and fill in their own secrets
- Each person keeps their `.env` locally (never commits it)

---

**Important:**
- ✅ Commit: `.env.example`, `.gitignore`, source code
- ❌ Never commit: `.env` (actual secrets)
- ✅ Git will automatically ignore `.env` thanks to `.gitignore`
