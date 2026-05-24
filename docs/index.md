# Python Computer Visoion — Advanced Tutorials

> **A comprehensive collection of production-grade automation scripts** covering file systems, web scraping, browser automation, Excel/CSV processing, email, scheduling, APIs, and more.

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)
[![Author](https://img.shields.io/badge/Author-Ashish%20Bindra-blue?style=for-the-badge&logo=github)](https://github.com/ashishbindra2)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin)](https://in.linkedin.com/in/ashishbindra2)

---

1. YOLO
2. CV2
3. Pillow

---

**Example — GitHub API: Auto-create Issue:**

```python
import requests

TOKEN = "your_github_token"
REPO  = "ashishbindra2/automation"

def create_issue(title, body, labels=None):
    url = f"https://api.github.com/repos/{REPO}/issues"
    headers = {"Authorization": f"token {TOKEN}"}
    data = {"title": title, "body": body, "labels": labels or []}
    r = requests.post(url, json=data, headers=headers)
    print(f"Issue created: {r.json()['html_url']}")

create_issue("Bug: Script fails on Windows", "Traceback...", ["bug"])
```

---

**Example — Kill process by name:**

```python
import psutil

def kill_process(name):
    for proc in psutil.process_iter(["name", "pid"]):
        if proc.info["name"] == name:
            proc.kill()
            print(f"Killed {name} (PID {proc.info['pid']})")

kill_process("chrome.exe")
```

---

### Environment Variables

Create a `.env` file in the root:

```env
EMAIL_USER=your@gmail.com
EMAIL_PASS=your_app_password
GITHUB_TOKEN=ghp_xxxxxxxxxxxx
```

Load in any script with:

```python
from dotenv import load_dotenv
import os
load_dotenv()
EMAIL_USER = os.getenv("EMAIL_USER")
```

---

## 🤝 Contributing

Pull requests are welcome! For major changes, open an issue first.

1. Fork the repo
2. Create your feature branch: `git checkout -b feature/new-script`
3. Commit: `git commit -m "Add: new automation script"`
4. Push: `git push origin feature/new-script`
5. Open a Pull Request

---

<div align="center">

Made with ❤️ by [Ashish Bindra](https://github.com/ashishbindra2) · [LinkedIn](https://in.linkedin.com/in/ashishbindra2) · [Twitter](https://twitter.com/bindra_ashish)

⭐ **Star this repo** if it helped you!

</div>
