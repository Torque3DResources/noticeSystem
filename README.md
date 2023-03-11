# Notice System
Uses Torques [RPC](https://www.techtarget.com/searchapparchitecture/definition/Remote-Procedure-Call-RPC) generating methods for notices and chat functionality.
Also leverages callOnModules() to layer one gui over another at runtime
# Assumed Knowlegde
https://docs.torque3d.org/for-programmers/networking/client-and-server-commands

# Usage and Instructions

### Installation
Copy entire noticeSystem folder into the Torque3D project's data/ folder, restart the project if it's running and it'll be integrated.

### method list
`function noticeSystem::Playgui_onWake()`

 callback. injects noticesystem gui elements on top of the playgui when it wakes up
 
`function noticeSystem::Playgui_onSleep()`

 callback. puts noticesystem gui elements to sleep when playgui is
 
`function noticeSystem::Playgui_clearHud()`

 callback. hides noticesystem gui elements when the hud is cleared

`function refreshBottomTextCtrl()`

`function refreshCenterTextCtrl()`

`function showPlayerList(%val)`

`function clientCmdChatMessage(%sender, %voice, %pitch, %msgString, %a1, %a2, %a3, %a4, %a5, %a6, %a7, %a8, %a9, %a10)`

 rpc. client side reciever
 
`function clientCmdServerMessage(%msgType, %msgString, %a1, %a2, %a3, %a4, %a5, %a6, %a7, %a8, %a9, %a10)`

 rpc. client side reciever
 
`function addMessageCallback(%msgType, %func)`

`function onServerMessage(%a, %b, %c, %d, %e, %f, %g, %h, %i)`

callback

`function defaultMessageCallback(%msgType, %msgString, %a1, %a2, %a3, %a4, %a5, %a6, %a7, %a8, %a9, %a10)`

`function MessageHud::open(%this)`

`function MessageHud::close(%this)`

`function MessageHud::toggleState(%this)`

`function MessageHud_Edit::onEscape(%this)`

`function MessageHud_Edit::eval(%this)`

    `commandToServer('teamMessageSent', %text);`
    
    `commandToServer('messageSent', %text);`

`function toggleMessageHud(%make)`

`function teamMessageHud(%make)`

`function clientCmdCenterPrint( %message, %time, %size )`

 rpc. client side reciever
 
`function clientCmdBottomPrint( %message, %time, %size )`

 rpc. client side reciever
 
`function BottomPrintText::onResize(%this, %width, %height)`

 callback. 
 
`function CenterPrintText::onResize(%this, %width, %height)`

 callback. 
 
`function clientCmdClearCenterPrint()`

 rpc. client side reciever
 
`function clientCmdClearBottomPrint()`

 rpc. client side reciever
 
`function playMessageSound(%message, %voice, %pitch)`

`function onChatMessage(%message, %voice, %pitch)`

 callback. 
 
`function onServerMessage(%message)`

 callback. 

`function MainChatHud::onWake( %this )`

 callback. 
 
`function MainChatHud::setChatHudLength( %this, %length )`

`function MainChatHud::nextChatHudLen( %this )`

`function ChatHud::addLine(%this,%text)`

`function ChatHud::pageUp(%this)`

`function ChatHud::pageDown(%this)`

`function pageUpMessageHud()`

`function pageDownMessageHud()`

`function cycleMessageHudSize()`

`function serverCmdTeamMessageSent(%client, %text)`

`function serverCmdMessageSent(%client, %text)`

`function centerPrintAll( %message, %time, %lines )`

    commandToClient( %cl, 'centerPrint', %message, %time, %lines );
    
 rpc. server side sender
 
`function bottomPrintAll( %message, %time, %lines )`

    commandToClient( %cl, 'bottomPrint', %message, %time, %lines );
    
 rpc. server side sender
 
`function centerPrint( %client, %message, %time, %lines )`

    commandToClient( %client, 'CenterPrint', %message, %time, %lines );
    
 rpc. server side sender
 
`function bottomPrint( %client, %message, %time, %lines )`

    commandToClient( %client, 'BottomPrint', %message, %time, %lines );
    
 rpc. server side sender
 
`function clearCenterPrint( %client )`

    commandToClient( %client, 'ClearCenterPrint');
    
 rpc. server side sender
 
`function clearBottomPrint( %client )`

    commandToClient( %client, 'ClearBottomPrint');
    
 rpc. server side sender
 
`function clearCenterPrintAll()`

    commandToClient( %cl, 'ClearCenterPrint');
    
 rpc. server side sender
 
`function clearBottomPrintAll()`

    commandToClient( %cl, 'ClearBottomPrint');
    
 rpc. server side sender
 
`function GameConnection::spamMessageTimeout(%this)`

 callback. 
 
`function GameConnection::spamReset(%this)`

`function spamAlert(%client)`

`function chatMessageClient( %client, %sender, %voiceTag, %voicePitch, %msgString, %a1, %a2, %a3, %a4, %a5, %a6, %a7, %a8, %a9, %a10 )`

    commandToClient( %client, 'ChatMessage', %sender, %voiceTag, %voicePitch, %msgString, %a1, %a2, %a3, %a4, %a5, %a6, %a7, %a8, %a9, %a10 );
    
 rpc. server side sender
 
`function chatMessageTeam( %sender, %team, %msgString, %a1, %a2, %a3, %a4, %a5, %a6, %a7, %a8, %a9, %a10 )`

`function chatMessageAll( %sender, %msgString, %a1, %a2, %a3, %a4, %a5, %a6, %a7, %a8, %a9, %a10 )`

`function handleClientJoin(%msgType, %msgString, %clientName, %clientId, %guid, %score, %kills, %deaths, %isAI, %isAdmin, %isSuperAdmin)`

 callback.
 
`function handleClientDrop(%msgType, %msgString, %clientName, %clientId)`

 callback.
 
`function handleClientScoreChanged(%msgType, %msgString, %score, %kills, %deaths, %clientId)`

 callback.

`function PlayerListGui::update(%this, %clientId, %name, %isSuperAdmin, %isAdmin, %isAI, %score, %kills, %deaths)`

`function PlayerListGui::updateScore(%this, %clientId, %score, %kills, %deaths)`

`function PlayerListGui::remove(%this, %clientId)`

`function PlayerListGui::toggle(%this)`

`function PlayerListGui::clear(%this)`

`function PlayerListGui::zeroScores(%this)`
