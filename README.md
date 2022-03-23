# Notice System
Uses Torques [RPC](https://www.techtarget.com/searchapparchitecture/definition/Remote-Procedure-Call-RPC) generating methods for notices and chat functionality.
Also leverages callOnModules() to layer one gui over another at runtime
 
# Usage and Instructions

### Installation
Copy entire noticeSystem folder into the Torque3D project's data/ folder, restart the project if it's running and it'll be integrated.

## RPC Samples:
### Sending a message from the server to a specific client
Server side command:
```
function centerPrint( %client, %message, %time, %lines )
{...      
   //tell a given %client to do the thing
   commandToClient( %client, 'CenterPrint', %message, %time, %lines );
}
```

Client side command:
```
function clientCmdCenterPrint( %message, %time, %size )
{...
   //do the thing
}
```

Per above, when calling commandToClient(), the command name 'CenterPrint' is a tag string, using only single quotations.
This tag string is combined with the standard "clientCmd" prefix to build the full name of the callback function on the client to receive the RPC command.
Parameters are otherwise passed normally.

### Sending a message from a client to the server
Client side command:
```
function MessageHud_Edit::eval(%this)
{...
   //ask the server to do the thing
commandToServer('messageSent', %text);
}
```

Server side command:
```
function serverCmdMessageSent(%client, %text)
{...
   //%client wants us to do the thing
}
```

Like sending from server to client, the tagged 'messageSent' command name is used with the standard "serverCmd" prefix to assemble the callback function name.
Unlike when sending from the server to a client, the client doesn't need to specify a server target in the arguments because there's only the one server.

## callOnModule callbacks
Uses the core callOnModules function to signal to any modules active that we have a particular event happening. It behaves akin to a regular signal-listen system.
Here, we indicate to all active modules that the event Playgui_onWake() when the PlayGUI wakes up.

```
function PlayGui::onWake(%this)
{...
   callOnModules("Playgui_onWake");
}
```

The notice system module then can respond to this via the matched callback function and do it's own behavior.
In our example, it will push the MainChatHUD gui element to the Canvas stack so it will display, as well as prep the message vector.
```
function noticeSystem::Playgui_onWake()
{
   // Message hud dialog
   if ( isObject( MainChatHud ) )
   {
      Canvas.pushDialog( MainChatHud );
      chatHud.attach(HudMessageVector);
   }
   ...
}
```

Another event, "Playgui_onSleep" is called when the PlayGui goes to sleep, allowing the notice system to pop MainChatHud from the canvas stack.


