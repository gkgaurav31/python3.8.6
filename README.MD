### Configuration Files

#### D:\home\site\applicationHost.xdt

```xml
<?xml version="1.0"?>
<configuration xmlns:xdt="http://schemas.microsoft.com/XML-Document-Transform">
  <system.webServer>
    <fastCgi>
      <application fullPath="D:\home\python3.8.6\python.exe" xdt:Locator="Match(fullPath)" xdt:Transform="Remove" />
      <application fullPath="D:\home\python3.8.6\python.exe" arguments="D:\home\python3.8.6\Lib\site-packages\wfastcgi.py"  maxInstances="0" xdt:Transform="Insert"/>
    </fastCgi>
  </system.webServer>
</configuration>
```

#### D:\home\site\wwwroot\web.config

```xml
<configuration>
  <appSettings>
    <add key="PYTHONPATH" value="D:\home\site\wwwroot"/>
    <!-- The handler here is specific to Bottle; other frameworks vary. -->
    <add key="WSGI_HANDLER" value="app.app"/>
    <add key="WSGI_LOG" value="D:\home\LogFiles\wfastcgi.log"/>
  </appSettings>
<system.webServer>
     <handlers>
          <remove name="Python38_via_FastCGI"/>
          <add name="Python38_via_FastCGI" path="*" verb="*" modules="FastCgiModule" 
          scriptProcessor="D:\home\python3.8.6\Python.exe|D:\home\python3.8.6\Lib\site-packages\wfastcgi.py" 
          resourceType="Unspecified" requireAccess="Script" />
     </handlers>
</system.webServer>
</configuration>
```
