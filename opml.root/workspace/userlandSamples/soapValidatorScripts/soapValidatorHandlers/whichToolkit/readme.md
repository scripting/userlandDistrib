### workspace.userlandSamples.soapValidatorScripts.soapValidatorHandlers.whichToolkit
<pre>
local (struct)
new (tabletype, @struct)
if system.environment.ispike
   struct.toolkitName = "Radio UserLand"
else
   struct.toolkitName = "UserLand Frontier"
struct.toolkitVersion = frontier.version ()
struct.toolkitDocsUrl = "http://radio.userland.com/soap"
struct.toolkitOperatingSystem = system.environment.osFullNameForDisplay + " " + system.environment.osVersionString
return (struct)

</pre>