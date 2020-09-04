```
<form theme="dark">
  <label>Truvis-Suricata Entire Network Overview</label>
  <fieldset submitButton="false">
    <input type="time" token="field1">
      <label>Time Frame</label>
      <default>
        <earliest>-24h@h</earliest>
        <latest>now</latest>
      </default>
    </input>
    <input type="text" token="field2">
      <label>SRC IP to Search</label>
      <default>*</default>
      <initialValue>*</initialValue>
    </input>
    <input type="text" token="field3">
      <label>DEST IP to Search</label>
      <default>*</default>
      <initialValue>*</initialValue>
    </input>
    <input type="multiselect" token="multi_select2" searchWhenChanged="true">
      <label>Suricata Events Organized Field Section:</label>
      <choice value="_time">_time</choice>
      <choice value="severity">severity</choice>
      <choice value="category">category</choice>
      <choice value="alert.signature_id">alert.signature_id</choice>
      <choice value="signature">signature</choice>
      <choice value="src_ip">src_ip</choice>
      <choice value="src_port">src_port</choice>
      <choice value="dest_ip">dest_ip</choice>
      <choice value="dest_port">dest_port</choice>
      <choice value="proto">proto</choice>
      <choice value="action">action</choice>
      <default>_time,severity,category,alert.signature_id,signature,src_ip,src_port,dest_ip,dest_port,proto,action</default>
      <delimiter>, </delimiter>
      <fieldForLabel>column</fieldForLabel>
      <fieldForValue>column</fieldForValue>
      <search>
        <query>index="suricata" sourcetype="suricata:alert" | stats values(*) AS * | transpose | table column</query>
      </search>
    </input>
    <input type="text" token="field4" searchWhenChanged="true">
      <label># Rows</label>
      <default>5</default>
      <initialValue>5</initialValue>
    </input>
    <input type="text" token="field5">
      <label>SRC IP to Exclude</label>
    </input>
    <input type="text" token="field6">
      <label>DEST IP to  Exclude</label>
    </input>
  </fieldset>
  <row>
    <panel>
      <single>
        <search>
          <query>index="suricata" sourcetype="suricata:alert" severity_id=1 src_ip="$field2$" dest_ip="$field3$" | stats count</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
          <sampleRatio>1</sampleRatio>
        </search>
        <option name="colorMode">block</option>
        <option name="drilldown">none</option>
        <option name="height">80</option>
        <option name="rangeColors">["0xdc4e41","0xdc4e41"]</option>
        <option name="rangeValues">[0]</option>
        <option name="underLabel">CRITICAL ALERTS</option>
        <option name="useColors">1</option>
      </single>
    </panel>
    <panel>
      <single>
        <search>
          <query>index="suricata" sourcetype="suricata:alert" severity_id=2 src_ip="$field2$" dest_ip="$field3$" | stats count(severity_id)</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
          <sampleRatio>1</sampleRatio>
        </search>
        <option name="colorMode">block</option>
        <option name="drilldown">none</option>
        <option name="height">80</option>
        <option name="rangeColors">["0xf1813f","0xf1813f"]</option>
        <option name="rangeValues">[0]</option>
        <option name="refresh.display">progressbar</option>
        <option name="underLabel">HIGH ALERTS</option>
        <option name="useColors">1</option>
      </single>
    </panel>
    <panel>
      <single>
        <search>
          <query>index="suricata" sourcetype="suricata:alert" severity_id=3 src_ip="$field2$" dest_ip="$field3$" | stats count(severity_id)</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
          <sampleRatio>1</sampleRatio>
        </search>
        <option name="colorMode">block</option>
        <option name="drilldown">none</option>
        <option name="height">80</option>
        <option name="rangeColors">["0xf8be34","0xf8be34"]</option>
        <option name="rangeValues">[0]</option>
        <option name="underLabel">MEDIUM ALERTS</option>
        <option name="useColors">1</option>
      </single>
    </panel>
    <panel>
      <single>
        <search>
          <query>index="suricata" sourcetype="suricata:alert" severity_id=4 src_ip="$field2$" dest_ip="$field3$" | stats count(severity_id)</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
          <sampleRatio>1</sampleRatio>
        </search>
        <option name="colorMode">block</option>
        <option name="drilldown">none</option>
        <option name="height">80</option>
        <option name="rangeColors">["0x53a051","0x53a051"]</option>
        <option name="rangeValues">[0]</option>
        <option name="refresh.display">progressbar</option>
        <option name="underLabel">LOW ALERTS</option>
        <option name="useColors">1</option>
      </single>
    </panel>
    <panel>
      <single>
        <search>
          <query>index="suricata" sourcetype="suricata:alert" severity_id=5 src_ip="$field2$" dest_ip="$field3$" | stats count(severity_id)</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
          <sampleRatio>1</sampleRatio>
        </search>
        <option name="colorMode">block</option>
        <option name="drilldown">none</option>
        <option name="height">80</option>
        <option name="rangeColors">["0x006d9c","0x006d9c"]</option>
        <option name="rangeValues">[0]</option>
        <option name="underLabel">INFO ALERTS</option>
        <option name="useColors">1</option>
      </single>
    </panel>
  </row>
  <row>
    <panel>
      <chart>
        <title>Alerts over time</title>
        <search>
          <query>index="suricata" sourcetype="suricata:alert" src_ip="$field2$" dest_ip="$field3$" | timechart count by severity</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
          <sampleRatio>1</sampleRatio>
        </search>
        <option name="charting.axisLabelsX.majorLabelStyle.overflowMode">ellipsisNone</option>
        <option name="charting.axisLabelsX.majorLabelStyle.rotation">0</option>
        <option name="charting.axisTitleX.visibility">visible</option>
        <option name="charting.axisTitleY.visibility">visible</option>
        <option name="charting.axisTitleY2.visibility">visible</option>
        <option name="charting.axisX.abbreviation">none</option>
        <option name="charting.axisX.scale">linear</option>
        <option name="charting.axisY.abbreviation">none</option>
        <option name="charting.axisY.scale">linear</option>
        <option name="charting.axisY2.abbreviation">none</option>
        <option name="charting.axisY2.enabled">0</option>
        <option name="charting.axisY2.scale">inherit</option>
        <option name="charting.chart">column</option>
        <option name="charting.chart.bubbleMaximumSize">50</option>
        <option name="charting.chart.bubbleMinimumSize">10</option>
        <option name="charting.chart.bubbleSizeBy">area</option>
        <option name="charting.chart.nullValueMode">gaps</option>
        <option name="charting.chart.showDataLabels">none</option>
        <option name="charting.chart.sliceCollapsingThreshold">0.01</option>
        <option name="charting.chart.stackMode">default</option>
        <option name="charting.chart.style">shiny</option>
        <option name="charting.drilldown">none</option>
        <option name="charting.layout.splitSeries">0</option>
        <option name="charting.layout.splitSeries.allowIndependentYRanges">0</option>
        <option name="charting.legend.labelStyle.overflowMode">ellipsisMiddle</option>
        <option name="charting.legend.mode">standard</option>
        <option name="charting.legend.placement">right</option>
        <option name="charting.lineWidth">2</option>
        <option name="refresh.display">progressbar</option>
        <option name="trellis.enabled">0</option>
        <option name="trellis.scales.shared">1</option>
        <option name="trellis.size">medium</option>
      </chart>
    </panel>
  </row>
  <row>
    <panel>
      <chart>
        <title>Signatures</title>
        <search>
          <query>index="suricata" sourcetype="suricata:alert" src_ip="$field2$" dest_ip="$field3$" | stats count by signature</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
          <sampleRatio>1</sampleRatio>
        </search>
        <option name="charting.axisTitleX.visibility">visible</option>
        <option name="charting.axisTitleY.visibility">visible</option>
        <option name="charting.axisTitleY2.visibility">visible</option>
        <option name="charting.chart">pie</option>
        <option name="charting.chart.nullValueMode">connect</option>
        <option name="charting.chart.sliceCollapsingThreshold">0</option>
        <option name="charting.chart.stackMode">stacked</option>
        <option name="charting.chart.style">shiny</option>
        <option name="charting.drilldown">none</option>
        <option name="charting.layout.splitSeries">1</option>
        <option name="charting.legend.placement">right</option>
        <option name="height">350</option>
      </chart>
    </panel>
    <panel>
      <chart>
        <title>Categories</title>
        <search>
          <query>index="suricata" sourcetype="suricata:alert" src_ip="$field2$" dest_ip="$field3$" | stats count by category</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
          <sampleRatio>1</sampleRatio>
        </search>
        <option name="charting.chart">pie</option>
        <option name="charting.drilldown">none</option>
        <option name="height">350</option>
      </chart>
    </panel>
  </row>
  <row>
    <panel>
      <chart>
        <title>Hits on ports</title>
        <search>
          <query>index="suricata" sourcetype="suricata:alert" src_ip="$field2$" dest_ip="$field3$" | stats count by dest_port</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
          <sampleRatio>1</sampleRatio>
        </search>
        <option name="charting.chart">pie</option>
        <option name="charting.chart.sliceCollapsingThreshold">0</option>
        <option name="charting.drilldown">none</option>
        <option name="height">350</option>
        <option name="refresh.display">progressbar</option>
      </chart>
    </panel>
    <panel>
      <chart>
        <title>Actions</title>
        <search>
          <query>index="suricata" sourcetype="suricata:alert" src_ip="$field2$" dest_ip="$field3$" | stats count by action</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
          <sampleRatio>1</sampleRatio>
        </search>
        <option name="charting.chart">pie</option>
        <option name="charting.drilldown">none</option>
        <option name="height">350</option>
      </chart>
    </panel>
  </row>
  <row>
    <panel>
      <chart>
        <title>Hits from SRC_IPs</title>
        <search>
          <query>index="suricata" sourcetype="suricata:alert" | stats count by src_ip</query>
          <earliest>-24h@h</earliest>
          <latest>now</latest>
        </search>
        <option name="charting.chart">pie</option>
        <option name="charting.drilldown">none</option>
        <option name="height">350</option>
      </chart>
    </panel>
    <panel>
      <chart>
        <title>Hits to DEST_IPs</title>
        <search>
          <query>index="suricata" sourcetype="suricata:alert" | stats count by dest_ip</query>
          <earliest>-24h@h</earliest>
          <latest>now</latest>
        </search>
        <option name="charting.chart">pie</option>
        <option name="charting.drilldown">none</option>
        <option name="height">350</option>
      </chart>
    </panel>
  </row>
  <row>
    <panel>
      <table>
        <title>Suricata Events Organized</title>
        <search>
          <query>index="suricata" sourcetype="suricata:alert" src_ip="$field2$" dest_ip="$field3$" | table $multi_select2$ | sort _time desc</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
          <sampleRatio>1</sampleRatio>
        </search>
        <option name="count">$field4$</option>
        <option name="dataOverlayMode">none</option>
        <option name="drilldown">cell</option>
        <option name="percentagesRow">false</option>
        <option name="rowNumbers">true</option>
        <option name="totalsRow">false</option>
      </table>
    </panel>
  </row>
  <row>
    <panel>
      <event>
        <title>Raw Events</title>
        <search>
          <query>index="suricata" sourcetype="suricata:alert" src_ip="$field2$" dest_ip="$field3$"</query>
          <earliest>$field1.earliest$</earliest>
          <latest>$field1.latest$</latest>
          <sampleRatio>1</sampleRatio>
        </search>
        <option name="count">$field4$</option>
        <option name="list.drilldown">full</option>
        <option name="list.wrap">1</option>
        <option name="maxLines">20</option>
        <option name="raw.drilldown">full</option>
        <option name="rowNumbers">1</option>
        <option name="table.drilldown">all</option>
        <option name="table.wrap">1</option>
        <option name="type">raw</option>
      </event>
    </panel>
  </row>
</form>
```
