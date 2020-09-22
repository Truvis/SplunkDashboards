<form theme="dark">
  <label>Truvis-Suricata Categories Overview [SUB]</label>
  <fieldset submitButton="false">
    <input type="time" token="field1" searchWhenChanged="true">
      <label>Time Frame</label>
      <default>
        <earliest>-24h@h</earliest>
        <latest>now</latest>
      </default>
    </input>
    <input type="dropdown" token="category" searchWhenChanged="true">
      <label>Category</label>
      <fieldForLabel>category</fieldForLabel>
      <fieldForValue>category</fieldForValue>
      <search>
        <query>index="suricata" sourcetype="suricata:alert" | fields category | dedup category | table category</query>
        <earliest>$field1.earliest$</earliest>
        <latest>$field1.latest$</latest>
        <refresh>30s</refresh>
        <refreshType>delay</refreshType>
      </search>
      <default>$cat$</default>
    </input>
  </fieldset>
  <row>
    <panel>
      <chart>
        <title>SRC IPS</title>
        <search>
          <query>index="suricata" sourcetype="suricata:alert" category="$category$" | stats count by src_ip</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
          <refresh>30s</refresh>
          <refreshType>delay</refreshType>
        </search>
        <option name="charting.chart">pie</option>
        <option name="charting.drilldown">none</option>
      </chart>
    </panel>
    <panel>
      <chart>
        <title>DEST IPS</title>
        <search>
          <query>index="suricata" sourcetype="suricata:alert" category="$category$" | stats count by dest_ip</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
          <refresh>30s</refresh>
          <refreshType>delay</refreshType>
        </search>
        <option name="charting.chart">pie</option>
        <option name="charting.drilldown">none</option>
      </chart>
    </panel>
    <panel>
      <chart>
        <title>PROTOCOL</title>
        <search>
          <query>index="suricata" sourcetype="suricata:alert" category="$category$"  | stats count by proto</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
          <refresh>30s</refresh>
          <refreshType>delay</refreshType>
        </search>
        <option name="charting.chart">pie</option>
        <option name="charting.drilldown">none</option>
      </chart>
    </panel>
    <panel>
      <chart>
        <title>Action</title>
        <search>
          <query>index="suricata" sourcetype="suricata:alert" category="$category$"  | stats count by action</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
          <refresh>30s</refresh>
          <refreshType>delay</refreshType>
        </search>
        <option name="charting.chart">pie</option>
        <option name="charting.drilldown">none</option>
      </chart>
    </panel>
  </row>
  <row>
    <panel>
      <table>
        <title>Connections</title>
        <search>
          <query>index="suricata" sourcetype="suricata:alert" category="$category$" 
| stats count by src_ip dest_ip dest_port transport
| stats list(dest_ip) as dest_ip list(dest_port) as dest_port list(transport) as transport list(count) as count by src_ip</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
          <refresh>30s</refresh>
          <refreshType>delay</refreshType>
        </search>
        <option name="drilldown">none</option>
        <option name="refresh.display">progressbar</option>
      </table>
    </panel>
  </row>
  <row>
    <panel>
      <event>
        <title>Raw Logs</title>
        <search>
          <query>index="suricata" sourcetype="suricata:alert" category="$category$"</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
          <refresh>30s</refresh>
          <refreshType>delay</refreshType>
        </search>
        <option name="list.drilldown">full</option>
        <option name="list.wrap">0</option>
        <option name="raw.drilldown">full</option>
        <option name="table.drilldown">none</option>
        <option name="table.wrap">0</option>
        <option name="type">raw</option>
      </event>
    </panel>
  </row>
</form>
