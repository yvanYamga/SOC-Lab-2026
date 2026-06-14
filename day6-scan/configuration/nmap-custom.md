=========================================================================
Custom rules NMAP

sudo nano /var/ossec/etc/rules/local_rules.xml

#########################################################################

<<group name="nmap,">
  <rule id="100001" level="10">
    <if_sid>1002</if_sid>
    <match>nmap|scan|portscan</match>
    <description>Nmap scan detected on endpoint</description>
    <mitre>
      <id>T1046</id>
    </mitre>
    <group>nmap,scan,reconnaissance,</group>
  </rule>
</group>

#########################################################################

sudo systemctl restart wazuh-manager
=========================================================================