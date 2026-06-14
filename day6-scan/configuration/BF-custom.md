==========================================================================
Custom rules Brute-force

sudo nano /var/ossec/etc/rules/local_rules.xml

##########################################################################

<<group name="ssh,">
  <rule id="100002" level="12">
    <if_matched_sid>5712</if_matched_sid>
    <frequency>5</frequency>
    <timeframe>120</timeframe>
    <description>SSH brute force attack - High severity</description>
    <mitre>
      <id>T1110</id>
    </mitre>
    <group>attack,brute_force,ssh,</group>
  </rule>
</group>

#########################################################################

sudo systemctl restart wazuh-manager

=========================================================================