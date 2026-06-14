===========================================================================
Config Agent-wazuh "windows"

<ossec_config>
  <client>
    <server>
      <address>VOTRE_IP_WAZUH</address>
      <port>1514</port>
      <protocol>tcp</protocol>
    </server>
  </client>
  
  <localfile>
    <location>Microsoft-Windows-Sysmon/Operational</location>
    <log_format>eventchannel</log_format>
  </localfile>
  
</ossec_config>

===========================================================================

Restart-Service -Name wazuh