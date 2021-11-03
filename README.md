# VizrtMSE.Plugin
> Vizrt MSE plugin for Cinegy EventManager


## Dependency
 - [Microsoft .NET Framework 4.6.1](https://www.microsoft.com/ru-ru/download/details.aspx?id=49982)
 - [Cinegy Event Manager](https://open.cinegy.com/products/air/21.9/cinegy-event-manager/)

## Install and Register
Unzip the VizrtMSE.Plugin.zip archive to C:\Program Files (x86)\Cinegy\3rd-party Event Plugins\
  
	PS> Expand-Archive -Path "VizrtMSE.Plugin.zip" -DestinationPath "C:\Program Files (x86)\Cinegy\3rd-party Event Plugins\"

Then you need to register the COM DLL:

	PS> cd C:\Windows\Microsoft.NET\Framework\v4.0.30319
	PS> RegAsm.exe "c:\Program Files (x86)\Cinegy\3rd-party Event Plugins\VizrtMSE.Plugin.dll" /codebase

![image](https://user-images.githubusercontent.com/93620683/139952545-d39d0528-ee42-42ad-8209-82044b1ecbd6.png)

## Uninstall and Un-register

	PS> cd C:\Windows\Microsoft.NET\Framework\v4.0.30319
	PS> RegAsm.exe "c:\Program Files (x86)\Cinegy\3rd-party Event Plugins\VizrtMSE.Plugin.dll" /u

![image](https://user-images.githubusercontent.com/93620683/139953024-a8119eaf-e74e-4671-93eb-c8b5eda15bc4.png)
	
	PS> cd "c:\Program Files (x86)\Cinegy\3rd-party Event Plugins\"
	PS> Remove-Item freehand.hwid.dll, Newtonsoft.Json.dll, VizrtMSE.Plugin.dll, VizrtMSE.Plugin.json


## Add EventService VIZRT_MSE to CinegyAir Pro
For you can modify a file:

	notepad.exe "C:\Program Files\Cinegy\Cinegy Air PRO (x64)\EventService.xml"

The content of the file will be the following one

    <?xml version="1.0"?>
    <ext_commands name="Event Service">
      <group name="Vizrt MSE">
        <command name="initialize">
          <event offset="+0" device="VIZRT_MSE" cmd="initialize"/>
        </command> 
        <command name="take">
          <event offset="+0" device="VIZRT_MSE" cmd="take"/>
        </command> 
        <command name="update">
          <event offset="+0" device="VIZRT_MSE" cmd="update"/>
        </command> 
        <command name="cut">
          <event offset="+0" device="VIZRT_MSE" cmd="cut"/>
        </command> 
        <command name="cut">
          <event offset="+0" device="VIZRT_MSE" cmd="cut"/>
        </command> 
        <command name="continue">
          <event offset="+0" device="VIZRT_MSE" cmd="continue"/>
        </command> 
        <command name="continue_reverse">
          <event offset="+0" device="VIZRT_MSE" cmd="continue_reverse"/>
        </command> 
        <command name="prepare">
          <event offset="+0" device="VIZRT_MSE" cmd="prepare"/>
        </command> 
        <command name="cue">
          <event offset="+0" device="VIZRT_MSE" cmd="cue"/>
        </command> 
        <command name="read">
          <event offset="+0" device="VIZRT_MSE" cmd="read"/>
        </command> 
        <command name="out">
          <event offset="+0" device="VIZRT_MSE" cmd="out"/>
        </command> 
      </group> 
      ...
      ...
    </ext_commands>
    
![image](https://user-images.githubusercontent.com/93620683/139954666-93b1d265-6de0-4b06-b37d-e680251fd91a.png)

![image](https://user-images.githubusercontent.com/93620683/139954818-9913cb3b-26f7-431a-84e5-003cdafe8b99.png)


`Device` `device`: must be `VIZRT_MSE`. (**required**)

`Command` `cmd`: vizrt MSE profile command. [More details [Vozrt MSE Documentation - Profile Command](http://127.0.0.1:8580/doc/profile_command.xhtml)] (**required**)

`Options1` `op1`: vizrt element name or desccription. (**required**)

`Options2` `op2`: vizrt playlist title. Usa Channel element_collection (Pages) if empty. (**optional**)

`Options3` `op3`: Channel Name. Default use from global settings Channel Name. (**optional**)

## Configure and Activate VizrtMSE Plugin
Run Event Manager Configurator application

    start "C:\Program Files (x86)\Cinegy\Cinegy Event Manager\EventsHandlerCfg.exe"
    
Select `Vizrt MSE Control` from Event Manager Plugins list

![image](https://user-images.githubusercontent.com/93620683/140023524-421cd9e0-5760-4b5a-8420-7cb22797048b.png)

To activate the plugin, select the `Active` checkbox

To configure the plugin, click `Setup` button

![image](https://user-images.githubusercontent.com/93620683/140023697-c78e7265-5c65-42a9-9714-754d9d4004a6.png)

`Vizrt MSE:` `Url` - Vizrt Media Sequencer REST API Url. (for example `http://VizrtMseHost:8580`)

`Vizrt MSE:` `Channel` - ``

`System:` `DebugMode` - activate the logging in debug mode (`C:\ProgramData\Cinegy\CinegyAir\EventServiceLog_*.log`)

`Licensing:` `HardwareID` - the computer hardware ID. 

## Licensing

The plugin must be registered, for more information contact the manufacturer of the plugin

![image](https://user-images.githubusercontent.com/93620683/140024173-c407b73f-b479-4e7f-a601-46b683ee60b5.png)


