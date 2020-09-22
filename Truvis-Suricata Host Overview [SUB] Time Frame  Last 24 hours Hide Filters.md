<form theme="dark">
  <label>Truvis-Suricata Host Overview [SUB]</label>
  <fieldset submitButton="false">
    <input type="time" token="field1" searchWhenChanged="true">
      <label>Time Frame</label>
      <default>
        <earliest>-24h@h</earliest>
        <latest>now</latest>
      </default>
    </input>
  </fieldset>
  <row>
    <panel>
      <chart>
        <title>Signatures</title>
        <search>
          <query>index=suricata src_ip="192.168.2.77" | stats count by alert.signature</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
        </search>
        <option name="charting.chart">pie</option>
        <option name="charting.drilldown">none</option>
        <option name="refresh.display">progressbar</option>
      </chart>
    </panel>
    <panel>
      <chart>
        <title>Categories</title>
        <search>
          <query>index=suricata src_ip="192.168.2.77" | stats count by alert.category</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
        </search>
        <option name="charting.chart">pie</option>
        <option name="charting.drilldown">none</option>
        <option name="refresh.display">progressbar</option>
      </chart>
    </panel>
    <panel>
      <chart>
        <title>Event Type</title>
        <search>
          <query>index=suricata src_ip="192.168.2.77" | stats count by event_type</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
        </search>
        <option name="charting.chart">pie</option>
        <option name="charting.drilldown">none</option>
        <option name="refresh.display">progressbar</option>
      </chart>
    </panel>
    <panel>
      <chart>
        <title>Anomalies</title>
        <search>
          <query>index=suricata sourcetype="suricata:anomaly" src_ip="192.168.2.77" | stats count by anomaly.event</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
        </search>
        <option name="charting.chart">pie</option>
        <option name="charting.drilldown">none</option>
        <option name="refresh.display">progressbar</option>
      </chart>
    </panel>
  </row>
  <row>
    <panel>
      <table>
        <title>Dest IPS</title>
        <search>
          <query>index=suricata sourcetype="suricata:flow"  src_ip="192.168.2.77" | stats count by dest_ip | table dest_ip count | sort - count</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
        </search>
        <option name="drilldown">none</option>
        <option name="refresh.display">progressbar</option>
      </table>
    </panel>
    <panel>
      <chart>
        <title>Dest Ports</title>
        <search>
          <query>index=suricata sourcetype="suricata:flow" src_ip="192.168.2.77" | stats count by dest_port</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
        </search>
        <option name="charting.chart">pie</option>
        <option name="charting.chart.sliceCollapsingThreshold">0</option>
        <option name="charting.drilldown">none</option>
        <option name="refresh.display">progressbar</option>
      </chart>
    </panel>
  </row>
  <row>
    <panel>
      <table>
        <title>Connections out to IPs</title>
        <search>
          <query>index=suricata sourcetype="suricata:flow" src_ip="192.168.2.77"
          |stats count by dest_ip dest_port proto
          |stats list(dest_port) as port list(proto) as proto list(count) as count by dest_ip | sort - count</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
        </search>
        <option name="drilldown">none</option>
        <option name="refresh.display">progressbar</option>
      </table>
    </panel>
  </row>
  <row>
    <panel>
      <table>
        <title>URIs Called</title>
        <search>
          <query>index=suricata sourcetype="suricata:http" src_ip="192.168.2.77" | stats count by url | table url count | sort - count</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
        </search>
        <option name="drilldown">none</option>
        <option name="refresh.display">progressbar</option>
      </table>
    </panel>
  </row>
  <row>
    <panel>
      <table>
        <title>Top DNS calls</title>
        <search>
          <query>index=suricata sourcetype="suricata:dns" src_ip="192.168.2.77" | stats count by dns.answers{}.rrname | table dns.answers{}.rrname count | sort - count</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
        </search>
        <option name="drilldown">none</option>
        <option name="refresh.display">progressbar</option>
      </table>
    </panel>
    <panel>
      <table>
        <title>URI Queries</title>
        <search>
          <query>index=suricata sourcetype="suricata:http" src_ip="192.168.2.77" | stats count by http.http_user_agent | table http.http_user_agent count | sort - count</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
        </search>
        <option name="drilldown">none</option>
        <option name="refresh.display">progressbar</option>
      </table>
    </panel>
  </row>
  <row>
    <panel>
      <event>
        <title>Anomaly Raw Logs</title>
        <search>
          <query>index=suricata sourcetype="suricata:anomaly" src_ip="192.168.2.77"</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
        </search>
        <option name="count">5</option>
        <option name="list.drilldown">full</option>
        <option name="raw.drilldown">full</option>
        <option name="table.drilldown">none</option>
        <option name="type">raw</option>
      </event>
    </panel>
  </row>
  <row>
    <panel>
      <event>
        <title>Alert Raw Lows</title>
        <search>
          <query>index=suricata sourcetype="suricata:alert" src_ip="192.168.2.77"</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
        </search>
        <option name="count">5</option>
        <option name="list.drilldown">none</option>
        <option name="raw.drilldown">none</option>
        <option name="type">raw</option>
      </event>
    </panel>
  </row>
</form>
