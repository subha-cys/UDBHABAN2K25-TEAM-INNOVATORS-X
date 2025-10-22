# UDBHABAN2K25
FACE RECOGNITION PROJECT FOR UDBHABAN 2025,RAAJDHANI ENGG. COLLEGE.
HERE IS THE WHOLE WORKING PROCESS TOOLS USE AND FUNCTIONING OF OUR SYSTEM.
Live face recognition (webcam / CCTV) with ArcFace (InsightFace) + face_recognition fallback

Requirements
- Python 3.11
- A virtualenv is recommended (the workspace already has `.venv` in this repo)

Install (PowerShell):

```powershell
& ".\.venv\Scripts\python.exe" -m pip install -r requirements.txt
```

Run with local webcam:

```powershell
& ".\.venv\Scripts\python.exe" "scripts/live_recognize.py" --camera 0
```

Run with RTSP/HTTP camera (CCTV):

```powershell
& ".\.venv\Scripts\python.exe" "scripts/live_recognize.py" --camera "rtsp://user:pass@192.168.1.10:554/stream"
```

If the network camera is unstable you can enable automatic reconnect attempts:

```powershell
& ".\.venv\Scripts\python.exe" "scripts/live_recognize.py" --camera "rtsp://user:pass@192.168.1.10:554/stream" --reconnect --reconnect-interval 5.0
```

Capture attendance
- Press SPACE while faces are detected to capture attendance. This will:
  - Save a snapshot to `data/attendance/`.
  - Append a CSV row to `data/attendance/attendance_log.csv`.
  - Append a row to `data/attendance.xlsx` (Log sheet) and mark present in Summary (requires `openpyxl`).

Notes
- If you see "OpenCV GUI not available" errors, install a GUI-enabled opencv package (e.g., `pip install opencv-python`) and avoid `opencv-python-headless`.
- For multi-process XLSX safety the script uses `filelock` to serialize writes. For high-throughput scenarios consider switching to SQLite or a central server.

Next steps (optional enhancements):
- Record first/last seen timestamps in the Summary sheet.
- Add auto-reconnect/backoff improvements and watchdogs for unstable streams.
- Provide a small web UI for attendance viewing.
