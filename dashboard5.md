```
<form theme="dark">
  <label>Truvis-Linux Host Dashboard</label>
  <fieldset submitButton="false">
    <input type="text" token="field1">
      <label>Host</label>
      <default>$clickedHOST$</default>
    </input>
    <input type="time" token="field2">
      <label>Time Frame</label>
      <default>
        <earliest>-24h@h</earliest>
        <latest>now</latest>
      </default>
    </input>
  </fieldset>
  <row>
    <panel>
      <table>
        <title>Successful Logons</title>
        <search>
          <query>source="/var/log/secure"  host="$field1$" sourcetype=linux_secure action=success  vendor_action=Accepted | table _time, src_ip, src_user, | sort - _time</query>
          <earliest>$field2.earliest$</earliest>
          <latest>$field2.latest$</latest>
          <sampleRatio>1</sampleRatio>
        </search>
        <option name="drilldown">none</option>
        <option name="refresh.display">progressbar</option>
        <format type="color" field="src_user">
          <colorPalette type="sharedList"></colorPalette>
          <scale type="sharedCategory"></scale>
        </format>
        <format type="color" field="src_ip">
          <colorPalette type="sharedList"></colorPalette>
          <scale type="sharedCategory"></scale>
        </format>
      </table>
    </panel>
    <panel>
      <table>
        <title>Current Open Sessions (including improperly closed)</title>
        <search>
          <query>source="/var/log/secure" host="$field1$" | transaction pid startswith="session opened" | regex _raw!="session closed" | table _time user</query>
          <earliest>$field2.earliest$</earliest>
          <latest>$field2.latest$</latest>
          <sampleRatio>1</sampleRatio>
        </search>
        <option name="drilldown">none</option>
      </table>
    </panel>
    <panel>
      <table>
        <title>Session Times (not including current)</title>
        <search>
          <query>source="/var/log/secure" host="$field1$" | transaction pid startswith="session opened" endswith="session closed" | eval HHMMSS=tostring(duration, "duration") | table _time user HHMMSS</query>
          <earliest>$field2.earliest$</earliest>
          <latest>$field2.latest$</latest>
          <sampleRatio>1</sampleRatio>
        </search>
        <option name="drilldown">none</option>
        <format type="color" field="user">
          <colorPalette type="sharedList"></colorPalette>
          <scale type="sharedCategory"></scale>
        </format>
      </table>
    </panel>
  </row>
  <row>
    <panel>
      <table>
        <title>Commands</title>
        <search>
          <query>sourcetype=bash_history host="$field1$" bash_command="./*" OR bash_command="sh *" | table _time, user_name, bash_command | sort - _time</query>
          <earliest>$field2.earliest$</earliest>
          <latest>$field2.latest$</latest>
          <sampleRatio>1</sampleRatio>
        </search>
        <option name="drilldown">none</option>
        <format type="color" field="user_name">
          <colorPalette type="sharedList"></colorPalette>
          <scale type="sharedCategory"></scale>
        </format>
      </table>
    </panel>
  </row>
  <row>
    <panel>
      <event>
        <title>Execute Command Events</title>
        <search>
          <query>sourcetype=bash_history host="$field1$" bash_command="./*" OR bash_command="sh *"</query>
          <earliest>$field2.earliest$</earliest>
          <latest>$field2.latest$</latest>
          <sampleRatio>1</sampleRatio>
        </search>
        <option name="list.drilldown">none</option>
      </event>
    </panel>
    <panel>
      <event>
        <title>Successful  Logon Events</title>
        <search>
          <query>source="/var/log/secure"  host="$field1$" sourcetype=linux_secure action=success  vendor_action=Accepted</query>
          <earliest>$field2.earliest$</earliest>
          <latest>$field2.latest$</latest>
          <sampleRatio>1</sampleRatio>
        </search>
        <option name="list.drilldown">none</option>
        <option name="refresh.display">progressbar</option>
      </event>
    </panel>
  </row>
</form>
```
