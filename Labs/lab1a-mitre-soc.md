**Part 1**
**Our log security file:**
[dashboard.py](https://github.com/user-attachments/files/29976608/dashboard.py)
2026-07-11T09:00:10 INFO User student logged in successfully from 172.18.0.10
2026-07-11T09:02:11 WARN Failed password for root from 172.18.0.5 port 44231 ssh2
2026-07-11T09:02:14 WARN Failed password for root from 172.18.0.5 port 44232 ssh2
2026-07-11T09:02:18 WARN Failed password for root from 172.18.0.5 port 44233 ssh2
2026-07-11T09:04:20 INFO Network scan detected from 172.18.0.7 against ports 22,80,443,3306
2026-07-11T09:07:33 INFO User administrator logged out

**The result of the final runnings:** 
{
  "generated_at": "2026-07-13T17:03:35.464956+00:00",
  "scan_interval_seconds": 5,
  "failed_password_threshold": 3,
  "finding_count": 2,
  "mitre_knowledge": {
    "source_file": "enterprise-attack-mini.json",
    "source_path": "/mitre/enterprise-attack-mini.json",
    "technique_count": 2,
    "loaded_at": "2026-07-13T16:05:20.278282+00:00",
    "file_modified_epoch": 1783948513.0,
    "status": "Loaded"
  },
  "findings": [
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.7",
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-11T09:04:20 INFO Network scan detected from 172.18.0.7 against ports 22,80,443,3306",
      "line_number": 5,
      "detection_rule": "The log contains 'network scan detected'.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible brute-force login attempt",
      "source_ip": "172.18.0.5",
      "failed_attempts": 3,
      "candidate_mitre_technique": "T1110",
      "severity": "High",
      "evidence": "3 failed password events were detected from 172.18.0.5.",
      "detection_rule": "At least 3 failed password events from the same source IP.",
      "mitre_technique": "T1110",
      "mitre_name": "Brute Force",
      "mitre_tactics": [
        "Credential Access"
      ],
      "tactic": "Credential Access",
      "mitre_url": "https://attack.mitre.org/techniques/T1110/",
      "mitre_stix_id": "attack-pattern--lab1a-t1110",
      "mitre_description": "Adversaries may use brute force techniques to gain access to accounts when passwords are unknown or when password hashes are obtained.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "1.7",
      "mitre_lookup_status": "Resolved from STIX"
    }
  ]
}

**Part 2 - Testing**
*Test A — Empty Log*
{
  "generated_at": "2026-07-13T16:57:32.007797+00:00",
  "scan_interval_seconds": 5,
  "failed_password_threshold": 3,
  "finding_count": 0,
  "mitre_knowledge": {
    "source_file": "enterprise-attack-mini.json",
    "source_path": "/mitre/enterprise-attack-mini.json",
    "technique_count": 2,
    "loaded_at": "2026-07-13T16:55:21.753003+00:00",
    "file_modified_epoch": 1783948513.0,
    "status": "Loaded"
  },
  "findings": []
}

*Test B — Brute-Force Pattern*
{
  "generated_at": "2026-07-13T17:12:36.676581+00:00",
  "scan_interval_seconds": 5,
  "failed_password_threshold": 3,
  "finding_count": 1,
  "mitre_knowledge": {
    "source_file": "enterprise-attack-mini.json",
    "source_path": "/mitre/enterprise-attack-mini.json",
    "technique_count": 2,
    "loaded_at": "2026-07-13T16:05:20.278282+00:00",
    "file_modified_epoch": 1783948513.0,
    "status": "Loaded"
  },
  "findings": [
    {
      "finding": "Possible brute-force login attempt",
      "source_ip": "172.18.0.20",
      "failed_attempts": 3,
      "candidate_mitre_technique": "T1110",
      "severity": "High",
      "evidence": "3 failed password events were detected from 172.18.0.20.",
      "detection_rule": "At least 3 failed password events from the same source IP.",
      "mitre_technique": "T1110",
      "mitre_name": "Brute Force",
      "mitre_tactics": [
        "Credential Access"
      ],
      "tactic": "Credential Access",
      "mitre_url": "https://attack.mitre.org/techniques/T1110/",
      "mitre_stix_id": "attack-pattern--lab1a-t1110",
      "mitre_description": "Adversaries may use brute force techniques to gain access to accounts when passwords are unknown or when password hashes are obtained.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "1.7",
      "mitre_lookup_status": "Resolved from STIX"
    }
  ]
}

*Test C — Network Scan Pattern*
{
  "generated_at": "2026-07-13T17:16:54.308718+00:00",
  "scan_interval_seconds": 5,
  "failed_password_threshold": 3,
  "finding_count": 1,
  "mitre_knowledge": {
    "source_file": "enterprise-attack-mini.json",
    "source_path": "/mitre/enterprise-attack-mini.json",
    "technique_count": 2,
    "loaded_at": "2026-07-13T16:55:21.753003+00:00",
    "file_modified_epoch": 1783948513.0,
    "status": "Loaded"
  },
  "findings": [
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.20",
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "Network scan detected from 172.18.0.20 against ports 22,80,443,3306",
      "line_number": 1,
      "detection_rule": "The log contains 'network scan detected'.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    }
  ]
}

*Test D — Synthetic Event Cycle*
*the new log file:*
Network scan detected from 172.18.0.20 against ports 22,80,443,33062026-07-13T17:18:23 WARN Failed password for root from 172.18.0.21 port 43889 ssh2
2026-07-13T17:18:23 WARN Failed password for root from 172.18.0.21 port 43890 ssh2
2026-07-13T17:18:23 WARN Failed password for root from 172.18.0.21 port 43891 ssh2
2026-07-13T17:18:33 WARN Failed password for root from 172.18.0.21 port 47466 ssh2
2026-07-13T17:18:33 WARN Failed password for root from 172.18.0.21 port 47467 ssh2
2026-07-13T17:18:33 WARN Failed password for root from 172.18.0.21 port 47468 ssh2
2026-07-13T17:18:43 INFO User student logged in successfully from 172.18.0.11

*the new Dashboard:*
[Uploadinfrom __future__ import annotations

import html
import json
from http.server import BaseHTTPRequestHandler, ThreadingHTTPServer
from pathlib import Path
from urllib.parse import urlparse

OUTPUT_PATH = Path("/output/findings.json")
LOG_PATH = Path("/data/security.log")


def load_snapshot() -> dict:
    try:
        data = json.loads(OUTPUT_PATH.read_text(encoding="utf-8"))
        if isinstance(data, dict):
            return data
    except Exception:
        pass

    return {
        "generated_at": "No detector output yet",
        "finding_count": 0,
        "mitre_knowledge": {
            "status": "Unknown",
            "source_file": None,
            "technique_count": 0,
            "loaded_at": None,
        },
        "findings": [],
    }


def load_log() -> str:
    try:
        return LOG_PATH.read_text(encoding="utf-8")
    except Exception:
        return "Raw log is not available."


def escape(value: object) -> str:
    return html.escape("" if value is None else str(value))


def render_page() -> str:
    snapshot = load_snapshot()
    findings = snapshot.get("findings", [])
    knowledge = snapshot.get("mitre_knowledge", {})
    raw_log = load_log()

    rows = []
    for index, item in enumerate(findings, start=1):
        technique = str(item.get("mitre_technique", ""))
        url = item.get("mitre_url") or (
            f"https://attack.mitre.org/techniques/{technique}/"
            if technique else "#"
        )
        tactics = item.get("mitre_tactics", [])
        if isinstance(tactics, list):
            tactic_text = ", ".join(str(x) for x in tactics)
        else:
            tactic_text = str(tactics)

        rows.append(
            "<tr>"
            f"<td>{index}</td>"
            f"<td>{escape(item.get('finding'))}</td>"
            f"<td>{escape(item.get('source_ip'))}</td>"
            f'<td><a href="{escape(url)}" target="_blank">'
            f"{escape(technique)} - {escape(item.get('mitre_name'))}"
            "</a></td>"
            f"<td>{escape(tactic_text)}</td>"
            f"<td>{escape(item.get('severity'))}</td>"
            f"<td>{escape(item.get('mitre_lookup_status'))}</td>"
            f"<td>{escape(item.get('evidence'))}</td>"
            "</tr>"
        )

    total = len(findings)
    high = sum(1 for x in findings if x.get("severity") == "High")
    medium = sum(
        1 for x in findings if x.get("severity") == "Medium"
    )

    return f"""<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta http-equiv="refresh" content="3">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Lab 1a SOC Dashboard</title>
<style>
body {{ font-family: Arial, sans-serif; margin: 24px; background: #f4f6f8; color: #1f2937; }}
h1 {{ margin-bottom: 6px; }}
.subtitle {{ color: #4b5563; margin-bottom: 8px; }}
.status {{ margin-bottom: 20px; }}
.cards {{ display: flex; gap: 16px; flex-wrap: wrap; margin-bottom: 24px; }}
.card {{ background: white; padding: 18px; border-radius: 10px; min-width: 180px; box-shadow: 0 2px 8px rgba(0,0,0,.08); }}
.card strong {{ font-size: 25px; display: block; margin-top: 6px; }}
table {{ width: 100%; border-collapse: collapse; background: white; box-shadow: 0 2px 8px rgba(0,0,0,.08); }}
th, td {{ border: 1px solid #d1d5db; padding: 9px; text-align: left; vertical-align: top; }}
th {{ background: #e5e7eb; }}
pre {{ background: #111827; color: #f9fafb; padding: 16px; border-radius: 10px; overflow-x: auto; }}
a {{ color: #1d4ed8; }}
</style>
</head>
<body>
<h1>Lab 1a SOC Dashboard</h1>
<div class="subtitle">Cyclic detection with periodic MITRE ATT&CK STIX refresh</div>
<div class="status">
<strong>Last detector scan:</strong> {escape(snapshot.get("generated_at"))}<br>
<strong>STIX status:</strong> {escape(knowledge.get("status"))}<br>
<strong>STIX source:</strong> {escape(knowledge.get("source_file") or "None")}<br>
<strong>Techniques loaded:</strong> {escape(knowledge.get("technique_count", 0))}<br>
<strong>STIX loaded at:</strong> {escape(knowledge.get("loaded_at") or "Not loaded")}
</div>

<div class="cards">
  <div class="card">Total findings<strong>{total}</strong></div>
  <div class="card">High severity<strong>{high}</strong></div>
  <div class="card">Medium severity<strong>{medium}</strong></div>
</div>

<h2>Detection Findings</h2>
<table>
<thead>
<tr>
<th>#</th><th>Activity</th><th>Source IP</th><th>MITRE ATT&CK</th>
<th>Tactic</th><th>Severity</th><th>STIX lookup</th><th>Evidence</th>
</tr>
</thead>
<tbody>
{''.join(rows) if rows else '<tr><td colspan="8">No findings detected.</td></tr>'}
</tbody>
</table>

<h2>Raw Security Log</h2>
<pre>{escape(raw_log)}</pre>
</body>
</html>"""


class Handler(BaseHTTPRequestHandler):
    def do_GET(self) -> None:
        if urlparse(self.path).path not in ("/", "/index.html"):
            self.send_error(404)
            return

        body = render_page().encode("utf-8")
        self.send_response(200)
        self.send_header("Content-Type", "text/html; charset=utf-8")
        self.send_header("Content-Length", str(len(body)))
        self.end_headers()
        self.wfile.write(body)

    def log_message(self, format: str, *args: object) -> None:
        print(format % args)


if __name__ == "__main__":
    server = ThreadingHTTPServer(("0.0.0.0", 8000), Handler)
    print("Dashboard running on http://0.0.0.0:8000", flush=True)
    server.serve_forever()
g dashboard.py…]()


**Part 3 - Required Changes**

**The changes:**
*docker-compose.yml*
added one line- NETWORK_SCAN_PORT_THRESHOLD: "4"

*detector.py new:*
import os

NETWORK_SCAN_PORT_THRESHOLD = int(
    os.getenv("NETWORK_SCAN_PORT_THRESHOLD", "4")
)
ports_text = line.split("against ports", 1)[1]
ports = [port.strip() for port in ports_text.split(",") if port.strip()]
if len(ports) >= NETWORK_SCAN_PORT_THRESHOLD:

"network_scan_port_threshold": NETWORK_SCAN_PORT_THRESHOLD

*deshboard.py*
Network Scan Port Threshold: 4
threshold = report.get("network_scan_port_threshold", "Not configured")
f"<div><strong>Network Scan Port Threshold:</strong> {threshold}</div>"

**the new output:**
{
  "generated_at": "2026-07-13T17:54:22.628296+00:00",
  "scan_interval_seconds": 5,
  "failed_password_threshold": 3,
  "network_scan_port_threshold": 4,
  "finding_count": 67,
  "mitre_knowledge": {
    "source_file": "enterprise-attack-mini.json",
    "source_path": "/mitre/enterprise-attack-mini.json",
    "technique_count": 2,
    "loaded_at": "2026-07-13T17:47:01.505208+00:00",
    "file_modified_epoch": 1783948513.0,
    "status": "Loaded"
  },
  "findings": [
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.20",
      "scanned_ports": [
        "22",
        "80",
        "443",
        "33062026-07-13T17:18:23 WARN Failed password for root from 172.18.0.21 port 43889 ssh2"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "Network scan detected from 172.18.0.20 against ports 22,80,443,33062026-07-13T17:18:23 WARN Failed password for root from 172.18.0.21 port 43889 ssh2",
      "line_number": 1,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.31",
      "scanned_ports": [
        "21",
        "22",
        "23",
        "25"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:19:23 INFO Network scan detected from 172.18.0.31 against ports 21,22,23,25",
      "line_number": 15,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.31",
      "scanned_ports": [
        "22",
        "80",
        "443",
        "3306"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:19:43 INFO Network scan detected from 172.18.0.31 against ports 22,80,443,3306",
      "line_number": 17,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.31",
      "scanned_ports": [
        "22",
        "80",
        "443",
        "3306"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:19:53 INFO Network scan detected from 172.18.0.31 against ports 22,80,443,3306",
      "line_number": 18,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.31",
      "scanned_ports": [
        "21",
        "22",
        "23",
        "25"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:20:23 INFO Network scan detected from 172.18.0.31 against ports 21,22,23,25",
      "line_number": 23,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.31",
      "scanned_ports": [
        "21",
        "22",
        "23",
        "25"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:20:53 INFO Network scan detected from 172.18.0.31 against ports 21,22,23,25",
      "line_number": 28,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.31",
      "scanned_ports": [
        "53",
        "80",
        "443",
        "8080"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:21:03 INFO Network scan detected from 172.18.0.31 against ports 53,80,443,8080",
      "line_number": 29,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.33",
      "scanned_ports": [
        "21",
        "22",
        "23",
        "25"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:21:23 INFO Network scan detected from 172.18.0.33 against ports 21,22,23,25",
      "line_number": 33,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.32",
      "scanned_ports": [
        "53",
        "80",
        "443",
        "8080"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:21:43 INFO Network scan detected from 172.18.0.32 against ports 53,80,443,8080",
      "line_number": 35,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.31",
      "scanned_ports": [
        "21",
        "22",
        "23",
        "25"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:22:13 INFO Network scan detected from 172.18.0.31 against ports 21,22,23,25",
      "line_number": 42,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.33",
      "scanned_ports": [
        "22",
        "80",
        "443",
        "3306"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:23:24 INFO Network scan detected from 172.18.0.33 against ports 22,80,443,3306",
      "line_number": 55,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.32",
      "scanned_ports": [
        "53",
        "80",
        "443",
        "8080"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:23:34 INFO Network scan detected from 172.18.0.32 against ports 53,80,443,8080",
      "line_number": 56,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.33",
      "scanned_ports": [
        "21",
        "22",
        "23",
        "25"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:24:14 INFO Network scan detected from 172.18.0.33 against ports 21,22,23,25",
      "line_number": 64,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.31",
      "scanned_ports": [
        "21",
        "22",
        "23",
        "25"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:25:44 INFO Network scan detected from 172.18.0.31 against ports 21,22,23,25",
      "line_number": 87,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.31",
      "scanned_ports": [
        "53",
        "80",
        "443",
        "8080"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:26:04 INFO Network scan detected from 172.18.0.31 against ports 53,80,443,8080",
      "line_number": 91,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.32",
      "scanned_ports": [
        "53",
        "80",
        "443",
        "8080"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:26:34 INFO Network scan detected from 172.18.0.32 against ports 53,80,443,8080",
      "line_number": 96,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.32",
      "scanned_ports": [
        "21",
        "22",
        "23",
        "25"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:29:04 INFO Network scan detected from 172.18.0.32 against ports 21,22,23,25",
      "line_number": 133,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.32",
      "scanned_ports": [
        "53",
        "80",
        "443",
        "8080"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:29:34 INFO Network scan detected from 172.18.0.32 against ports 53,80,443,8080",
      "line_number": 140,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.32",
      "scanned_ports": [
        "53",
        "80",
        "443",
        "8080"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:30:14 INFO Network scan detected from 172.18.0.32 against ports 53,80,443,8080",
      "line_number": 146,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.32",
      "scanned_ports": [
        "21",
        "22",
        "23",
        "25"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:31:14 INFO Network scan detected from 172.18.0.32 against ports 21,22,23,25",
      "line_number": 160,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.32",
      "scanned_ports": [
        "21",
        "22",
        "23",
        "25"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:33:14 INFO Network scan detected from 172.18.0.32 against ports 21,22,23,25",
      "line_number": 184,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.33",
      "scanned_ports": [
        "21",
        "22",
        "23",
        "25"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:33:34 INFO Network scan detected from 172.18.0.33 against ports 21,22,23,25",
      "line_number": 186,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.33",
      "scanned_ports": [
        "21",
        "22",
        "23",
        "25"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:34:24 INFO Network scan detected from 172.18.0.33 against ports 21,22,23,25",
      "line_number": 197,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.32",
      "scanned_ports": [
        "22",
        "80",
        "443",
        "3306"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:34:44 INFO Network scan detected from 172.18.0.32 against ports 22,80,443,3306",
      "line_number": 201,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.31",
      "scanned_ports": [
        "53",
        "80",
        "443",
        "8080"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:37:44 INFO Network scan detected from 172.18.0.31 against ports 53,80,443,8080",
      "line_number": 235,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.31",
      "scanned_ports": [
        "22",
        "80",
        "443",
        "3306"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:38:24 INFO Network scan detected from 172.18.0.31 against ports 22,80,443,3306",
      "line_number": 243,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.33",
      "scanned_ports": [
        "21",
        "22",
        "23",
        "25"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:39:34 INFO Network scan detected from 172.18.0.33 against ports 21,22,23,25",
      "line_number": 252,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.32",
      "scanned_ports": [
        "22",
        "80",
        "443",
        "3306"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:40:04 INFO Network scan detected from 172.18.0.32 against ports 22,80,443,3306",
      "line_number": 257,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.33",
      "scanned_ports": [
        "21",
        "22",
        "23",
        "25"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:40:24 INFO Network scan detected from 172.18.0.33 against ports 21,22,23,25",
      "line_number": 261,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.33",
      "scanned_ports": [
        "53",
        "80",
        "443",
        "8080"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:40:44 INFO Network scan detected from 172.18.0.33 against ports 53,80,443,8080",
      "line_number": 265,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.33",
      "scanned_ports": [
        "22",
        "80",
        "443",
        "3306"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:41:44 INFO Network scan detected from 172.18.0.33 against ports 22,80,443,3306",
      "line_number": 277,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.33",
      "scanned_ports": [
        "22",
        "80",
        "443",
        "3306"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:42:34 INFO Network scan detected from 172.18.0.33 against ports 22,80,443,3306",
      "line_number": 284,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.33",
      "scanned_ports": [
        "22",
        "80",
        "443",
        "3306"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:42:44 INFO Network scan detected from 172.18.0.33 against ports 22,80,443,3306",
      "line_number": 285,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.32",
      "scanned_ports": [
        "21",
        "22",
        "23",
        "25"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:42:54 INFO Network scan detected from 172.18.0.32 against ports 21,22,23,25",
      "line_number": 286,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.32",
      "scanned_ports": [
        "53",
        "80",
        "443",
        "8080"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:43:14 INFO Network scan detected from 172.18.0.32 against ports 53,80,443,8080",
      "line_number": 290,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.31",
      "scanned_ports": [
        "21",
        "22",
        "23",
        "25"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:43:34 INFO Network scan detected from 172.18.0.31 against ports 21,22,23,25",
      "line_number": 292,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.32",
      "scanned_ports": [
        "21",
        "22",
        "23",
        "25"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:43:54 INFO Network scan detected from 172.18.0.32 against ports 21,22,23,25",
      "line_number": 294,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.33",
      "scanned_ports": [
        "21",
        "22",
        "23",
        "25"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:44:04 INFO Network scan detected from 172.18.0.33 against ports 21,22,23,25",
      "line_number": 295,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.32",
      "scanned_ports": [
        "21",
        "22",
        "23",
        "25"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:44:14 INFO Network scan detected from 172.18.0.32 against ports 21,22,23,25",
      "line_number": 296,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.33",
      "scanned_ports": [
        "21",
        "22",
        "23",
        "25"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:44:34 INFO Network scan detected from 172.18.0.33 against ports 21,22,23,25",
      "line_number": 300,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.31",
      "scanned_ports": [
        "53",
        "80",
        "443",
        "8080"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:44:54 INFO Network scan detected from 172.18.0.31 against ports 53,80,443,8080",
      "line_number": 304,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.31",
      "scanned_ports": [
        "21",
        "22",
        "23",
        "25"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:45:44 INFO Network scan detected from 172.18.0.31 against ports 21,22,23,25",
      "line_number": 311,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.33",
      "scanned_ports": [
        "21",
        "22",
        "23",
        "25"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:46:34 INFO Network scan detected from 172.18.0.33 against ports 21,22,23,25",
      "line_number": 324,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.32",
      "scanned_ports": [
        "21",
        "22",
        "23",
        "25"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:46:54 INFO Network scan detected from 172.18.0.32 against ports 21,22,23,25",
      "line_number": 328,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.31",
      "scanned_ports": [
        "22",
        "80",
        "443",
        "3306"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:47:14 INFO Network scan detected from 172.18.0.31 against ports 22,80,443,3306",
      "line_number": 330,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.31",
      "scanned_ports": [
        "22",
        "80",
        "443",
        "3306"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:47:34 INFO Network scan detected from 172.18.0.31 against ports 22,80,443,3306",
      "line_number": 332,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.33",
      "scanned_ports": [
        "53",
        "80",
        "443",
        "8080"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:48:04 INFO Network scan detected from 172.18.0.33 against ports 53,80,443,8080",
      "line_number": 337,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.31",
      "scanned_ports": [
        "21",
        "22",
        "23",
        "25"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:49:14 INFO Network scan detected from 172.18.0.31 against ports 21,22,23,25",
      "line_number": 348,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.32",
      "scanned_ports": [
        "22",
        "80",
        "443",
        "3306"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:49:24 INFO Network scan detected from 172.18.0.32 against ports 22,80,443,3306",
      "line_number": 349,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.32",
      "scanned_ports": [
        "53",
        "80",
        "443",
        "8080"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:49:35 INFO Network scan detected from 172.18.0.32 against ports 53,80,443,8080",
      "line_number": 350,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.32",
      "scanned_ports": [
        "22",
        "80",
        "443",
        "3306"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:49:45 INFO Network scan detected from 172.18.0.32 against ports 22,80,443,3306",
      "line_number": 351,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.31",
      "scanned_ports": [
        "53",
        "80",
        "443",
        "8080"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:49:55 INFO Network scan detected from 172.18.0.31 against ports 53,80,443,8080",
      "line_number": 352,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.33",
      "scanned_ports": [
        "22",
        "80",
        "443",
        "3306"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:50:15 INFO Network scan detected from 172.18.0.33 against ports 22,80,443,3306",
      "line_number": 356,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.31",
      "scanned_ports": [
        "22",
        "80",
        "443",
        "3306"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:50:45 INFO Network scan detected from 172.18.0.31 against ports 22,80,443,3306",
      "line_number": 363,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.32",
      "scanned_ports": [
        "22",
        "80",
        "443",
        "3306"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:51:05 INFO Network scan detected from 172.18.0.32 against ports 22,80,443,3306",
      "line_number": 365,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.31",
      "scanned_ports": [
        "21",
        "22",
        "23",
        "25"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:51:15 INFO Network scan detected from 172.18.0.31 against ports 21,22,23,25",
      "line_number": 366,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.32",
      "scanned_ports": [
        "21",
        "22",
        "23",
        "25"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:51:45 INFO Network scan detected from 172.18.0.32 against ports 21,22,23,25",
      "line_number": 373,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.33",
      "scanned_ports": [
        "22",
        "80",
        "443",
        "3306"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:51:55 INFO Network scan detected from 172.18.0.33 against ports 22,80,443,3306",
      "line_number": 374,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.32",
      "scanned_ports": [
        "53",
        "80",
        "443",
        "8080"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:52:05 INFO Network scan detected from 172.18.0.32 against ports 53,80,443,8080",
      "line_number": 375,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.31",
      "scanned_ports": [
        "22",
        "80",
        "443",
        "3306"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:52:25 INFO Network scan detected from 172.18.0.31 against ports 22,80,443,3306",
      "line_number": 377,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.32",
      "scanned_ports": [
        "22",
        "80",
        "443",
        "3306"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:52:45 INFO Network scan detected from 172.18.0.32 against ports 22,80,443,3306",
      "line_number": 381,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.32",
      "scanned_ports": [
        "53",
        "80",
        "443",
        "8080"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:52:55 INFO Network scan detected from 172.18.0.32 against ports 53,80,443,8080",
      "line_number": 382,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.32",
      "scanned_ports": [
        "21",
        "22",
        "23",
        "25"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:53:55 INFO Network scan detected from 172.18.0.32 against ports 21,22,23,25",
      "line_number": 392,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible network service discovery",
      "source_ip": "172.18.0.32",
      "scanned_ports": [
        "22",
        "80",
        "443",
        "3306"
      ],
      "scanned_port_count": 4,
      "network_scan_port_threshold": 4,
      "candidate_mitre_technique": "T1046",
      "severity": "Medium",
      "evidence": "2026-07-13T17:54:15 INFO Network scan detected from 172.18.0.32 against ports 22,80,443,3306",
      "line_number": 394,
      "detection_rule": "At least 4 ports were listed in a network scan event.",
      "mitre_technique": "T1046",
      "mitre_name": "Network Service Discovery",
      "mitre_tactics": [
        "Discovery"
      ],
      "tactic": "Discovery",
      "mitre_url": "https://attack.mitre.org/techniques/T1046/",
      "mitre_stix_id": "attack-pattern--lab1a-t1046",
      "mitre_description": "Adversaries may attempt to identify services running on remote hosts and local network infrastructure.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "2.2",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible brute-force login attempt",
      "source_ip": "172.18.0.21",
      "failed_attempts": 95,
      "candidate_mitre_technique": "T1110",
      "severity": "High",
      "evidence": "95 failed password events were detected from 172.18.0.21.",
      "detection_rule": "At least 3 failed password events from the same source IP.",
      "mitre_technique": "T1110",
      "mitre_name": "Brute Force",
      "mitre_tactics": [
        "Credential Access"
      ],
      "tactic": "Credential Access",
      "mitre_url": "https://attack.mitre.org/techniques/T1110/",
      "mitre_stix_id": "attack-pattern--lab1a-t1110",
      "mitre_description": "Adversaries may use brute force techniques to gain access to accounts when passwords are unknown or when password hashes are obtained.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "1.7",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible brute-force login attempt",
      "source_ip": "172.18.0.22",
      "failed_attempts": 87,
      "candidate_mitre_technique": "T1110",
      "severity": "High",
      "evidence": "87 failed password events were detected from 172.18.0.22.",
      "detection_rule": "At least 3 failed password events from the same source IP.",
      "mitre_technique": "T1110",
      "mitre_name": "Brute Force",
      "mitre_tactics": [
        "Credential Access"
      ],
      "tactic": "Credential Access",
      "mitre_url": "https://attack.mitre.org/techniques/T1110/",
      "mitre_stix_id": "attack-pattern--lab1a-t1110",
      "mitre_description": "Adversaries may use brute force techniques to gain access to accounts when passwords are unknown or when password hashes are obtained.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "1.7",
      "mitre_lookup_status": "Resolved from STIX"
    },
    {
      "finding": "Possible brute-force login attempt",
      "source_ip": "172.18.0.23",
      "failed_attempts": 84,
      "candidate_mitre_technique": "T1110",
      "severity": "High",
      "evidence": "84 failed password events were detected from 172.18.0.23.",
      "detection_rule": "At least 3 failed password events from the same source IP.",
      "mitre_technique": "T1110",
      "mitre_name": "Brute Force",
      "mitre_tactics": [
        "Credential Access"
      ],
      "tactic": "Credential Access",
      "mitre_url": "https://attack.mitre.org/techniques/T1110/",
      "mitre_stix_id": "attack-pattern--lab1a-t1110",
      "mitre_description": "Adversaries may use brute force techniques to gain access to accounts when passwords are unknown or when password hashes are obtained.",
      "mitre_created": "2026-07-11T00:00:00.000Z",
      "mitre_modified": "2026-07-11T00:00:00.000Z",
      "mitre_version": "1.7",
      "mitre_lookup_status": "Resolved from STIX"
    }
  ]
}




