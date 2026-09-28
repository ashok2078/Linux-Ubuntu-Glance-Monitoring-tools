************  Practice & Testing (Simulating Load)************

To test warning and critical alert thresholds, you can use stress.

sudo apt install stress
stress --cpu 4 --timeout 60

EOF
<img width="2880" height="1000" alt="image" src="https://github.com/user-attachments/assets/290374a5-c391-484a-b6aa-9575fb1aa90c" />


### Step 3: Create the `NOTES.md` File
This file will hold troubleshooting notes, commands learned, and personal deployment logs. Run this command:

```bash
cat << 'EOF' > NOTES.md
# Project Development Notes & Troubleshooting

## 1. Environment Error Management (PEP 668)
- **Issue:** Modern Ubuntu versions restrict global `pip` installations with `externally-managed-environment` errors to protect system Python packages.
- **Solution:** Avoid `sudo pip3 install`. Instead, use `pipx` to isolate Python CLI applications into dedicated virtual environments automatically.

## 2. Web UI Missing Static Files Bug
- **Issue:** Installing glances via standard `sudo apt install glances` on certain Ubuntu releases results in a missing directory error: 
  `RuntimeError: Directory '.../outputs/static/public' does not exist`.
- **Solution:** Purge the apt version (`sudo apt remove --purge glances`) and install via `pipx install --force glances[web]` to include FastAPI components and static interface templates.

## 3. Useful Glances Shortcuts
- `c`: Sort processes by CPU usage.
- `m`: Sort processes by Memory usage.
- `i`: Sort processes by Disk I/O rate.
- `q`: Quit / exit.
EOF
