```
<dashboard theme="dark">
  <label>Truvis-Blocked Out Going Connections FROM IP BY port</label>
    <fieldset submitButton="false">
    <input type="time" token="field1">
      <label>Select Timeframe</label>
      <default>
        <earliest>-24h@h</earliest>
        <latest>now</latest>
      </default>
    </input>
    <input type="dropdown" token="dport" searchWhenChanged="true">
      <label>Select Port</label>
      <search>
        <query>sourcetype="opnsense:filterlog" action=blocked src_ip="$clickedIP$" | stats values(dest_port) as dport | mvexpand dport | sort dport</query>
      </search>
      <fieldForLabel>dport</fieldForLabel>
      <fieldForValue>dport</fieldForValue>
      <prefix></prefix>
      <suffix></suffix>
      <choice value="*">All</choice>
      <default>*</default>
    </input>
    <input type="dropdown" token="proto" searchWhenChanged="true">
      <label>Select Protocol</label>
      <search>
        <query>sourcetype="opnsense:filterlog" action=blocked src_ip="$clickedIP$" | stats values(transport) as proto | mvexpand proto | sort proto</query>
      </search>
      <fieldForLabel>proto</fieldForLabel>
      <fieldForValue>proto</fieldForValue>
      <prefix></prefix>
      <suffix></suffix>
      <choice value="*">All</choice>
      <default>*</default>
    </input>
  </fieldset>
  <row>
    <panel>
      <title>Local IPs count by blocked out going connections. (click for details)</title>
      <chart>
        <search>
          <query>sourcetype="opnsense:filterlog" action=blocked src_ip="$clickedIP$" dest_port="$dport$" transport="$proto$" | stats count(dest_port) as TotalBlockPorts by dest_port | sort TotalBlockPorts desc</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
          <sampleRatio>1</sampleRatio>
        </search>
        <option name="charting.axisLabelsX.majorLabelStyle.rotation">0</option>
        <option name="charting.axisY.abbreviation">none</option>
        <option name="charting.axisY.scale">linear</option>
        <option name="charting.chart">bar</option>
        <option name="charting.chart.showDataLabels">all</option>
        <option name="charting.chart.stackMode">default</option>
        <option name="charting.drilldown">all</option>
        <option name="charting.layout.splitSeries">0</option>
        <option name="charting.legend.placement">bottom</option>
        <option name="height">266</option>
        <option name="refresh.display">progressbar</option>
      </chart>
    </panel>
  </row>
  <row>
    <panel>
      <title>IPs to PORT</title>
      <table>
        <search>
          <query>sourcetype="opnsense:filterlog" action=blocked src_ip="$clickedIP$" dest_port="$dport$" transport="$proto$" | stats count(dest_port) as COUNT by dest_port, transport, dest_ip | table dest_port, transport, dest_ip, COUNT</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
          <sampleRatio>1</sampleRatio>
        </search>
        <option name="count">30</option>
        <option name="drilldown">cell</option>
        <format type="color" field="dest_port">
          <colorPalette type="sharedList"></colorPalette>
          <scale type="sharedCategory"></scale>
        </format>
        <format type="color" field="transport">
          <colorPalette type="sharedList"></colorPalette>
          <scale type="sharedCategory"></scale>
        </format>
        <format type="color" field="dest_ip">
          <colorPalette type="sharedList"></colorPalette>
          <scale type="sharedCategory"></scale>
        </format>
        <format type="color" field="COUNT">
          <colorPalette type="minMidMax" maxColor="#ff4c4c" midColor="#ff7f7f" minColor="#ffe5e5"></colorPalette>
          <scale type="minMidMax" maxType="percentile" maxValue="100" midType="percentile" midValue="50" minType="percentile" minValue="0"></scale>
        </format>
      </table>
    </panel>
    <panel>
      <event>
        <search>
          <query>sourcetype="opnsense:filterlog" action=blocked src_ip="$clickedIP$" dest_port="$dport$" transport="$proto$"</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
          <sampleRatio>1</sampleRatio>
        </search>
        <option name="list.drilldown">none</option>
        <option name="list.wrap">1</option>
        <option name="raw.drilldown">none</option>
        <option name="rowNumbers">0</option>
        <option name="table.drilldown">none</option>
        <option name="table.wrap">1</option>
        <option name="type">list</option>
      </event>
    </panel>
  </row>
</dashboard>
```
