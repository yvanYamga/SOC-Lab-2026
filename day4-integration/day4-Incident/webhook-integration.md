
---

### `day4-incident/webhook-integration.md`

```markdown
# Webhook Integration - Wazuh to External Endpoint

## Objective
Integrate Wazuh SIEM with external webhook for real-time alerting.

## Configuration

### Wazuh Integration Script
Location: `/var/ossec/integrations/custom-webhook.py`

```python
#!/usr/bin/env python3
import sys
import json
import requests

def main():
    # Read last alert from JSON file
    with open(sys.argv[1], 'r') as f:
        lines = f.readlines()
    
    # Parse last valid JSON line
    last_alert = None
    for line in reversed(lines):
        line = line.strip()
        if line:
            try:
                last_alert = json.loads(line)
                break
            except:
                continue
    
    if not last_alert:
        print("No valid alert found")
        sys.exit(1)
    
    webhook_url = "https://webhook.site/0cef6513-6be8-4b65-b694-81f2f9fe7ef4"
    
    payload = {
        "source": "wazuh",
        "alert_id": last_alert.get("id"),
        "rule": last_alert.get("rule", {}).get("description"),
        "level": last_alert.get("rule", {}).get("level"),
        "agent": last_alert.get("agent", {}).get("name"),
        "timestamp": last_alert.get("timestamp")
    }
    
    response = requests.post(webhook_url, json=payload, timeout=10)
    print(f"Webhook sent: {response.status_code}")

if __name__ == "__main__":
    main()

=======================================================================================
Wazuh configuration

File : /var/ossec/etc/ossec.conf

xml: 
<integration>
  <name>custom-webhook</name>
  <hook_url>https://webhook.site/0cef6513-6be8-4b65-b694-81f2f9fe7ef4</hook_url>
  <alert_format>json</alert_format>
  <level>7</level>
</integration>

=======================================================================================