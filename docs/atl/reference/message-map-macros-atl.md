---
title: "Message Map Macros (ATL) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: eefdd546-8934-4a30-b263-9c06a8addcbd
caps.latest.revision: 16
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Message Map Macros (ATL)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這些巨集定義訊息對應的和項目。  
  
|||  
|-|-|  
|[ALT\_MSG\_MAP](../Topic/ALT_MSG_MAP.md)|標記中使用一個替代的訊息對應的開頭。|  
|[BEGIN\_MSG\_MAP](../Topic/BEGIN_MSG_MAP.md)|標記預設的訊息對應的開頭。|  
|[CHAIN\_MSG\_MAP\_ALT](../Topic/CHAIN_MSG_MAP_ALT.md)|為替代訊息的鏈結在基底類別中的對應。|  
|[CHAIN\_MSG\_MAP\_ALT\_MEMBER](../Topic/CHAIN_MSG_MAP_ALT_MEMBER.md)|為替代訊息的鏈結到類別的資料成員會對應至。|  
|[CHAIN\_MSG\_MAP](../Topic/CHAIN_MSG_MAP.md)|對預設訊息的鏈結在基底類別中的對應。|  
|[CHAIN\_MSG\_MAP\_DYNAMIC](../Topic/CHAIN_MSG_MAP_DYNAMIC.md)|對訊息的鏈結到另一個類別對應於執行階段。|  
|[CHAIN\_MSG\_MAP\_MEMBER](../Topic/CHAIN_MSG_MAP_MEMBER.md)|對預設訊息的鏈結到類別的資料成員會對應至。|  
|[COMMAND\_CODE\_HANDLER](../Topic/COMMAND_CODE_HANDLER.md)|將 **WM\_COMMAND** 訊息至處理函式，以通知程式碼。|  
|[COMMAND\_HANDLER](../Topic/COMMAND_HANDLER.md)|將 **WM\_COMMAND** 訊息至處理函式，以通知程式碼和功能表項目、控制項或快速鍵的識別項。|  
|[COMMAND\_ID\_HANDLER](../Topic/COMMAND_ID_HANDLER.md)|將 **WM\_COMMAND** 訊息至處理函式，根據功能表項目、控制項或快速鍵的識別項。|  
|[COMMAND\_RANGE\_CODE\_HANDLER](../Topic/COMMAND_RANGE_CODE_HANDLER.md)|將 **WM\_COMMAND** 訊息至處理函式，以通知程式碼和控制識別項的一個連續範圍。|  
|[COMMAND\_RANGE\_HANDLER](../Topic/COMMAND_RANGE_HANDLER.md)|將 **WM\_COMMAND** 訊息至處理函式，根據控制識別項的一個連續範圍。|  
|[DECLARE\_EMPTY\_MSG\_MAP](../Topic/DECLARE_EMPTY_MSG_MAP.md)|實作一個空的訊息對應。|  
|[DEFAULT\_REFLECTION\_HANDLER](../Topic/DEFAULT_REFLECTION_HANDLER.md)|對於沒有要處理的反映訊息的預設處理常式。|  
|[END\_MSG\_MAP](../Topic/END_MSG_MAP.md)|標記訊息對應的結束。|  
|[FORWARD\_NOTIFICATIONS](../Topic/FORWARD_NOTIFICATIONS.md)|傳送通知訊息寫入父視窗。|  
|[MESSAGE\_HANDLER](../Topic/MESSAGE_HANDLER.md)|將 Windows 訊息至處理函式。|  
|[MESSAGE\_RANGE\_HANDLER](../Topic/MESSAGE_RANGE_HANDLER.md)|將 Windows 訊息的單一連續範圍至處理函式。|  
|[NOTIFY\_CODE\_HANDLER](../Topic/NOTIFY_CODE_HANDLER.md)|將 **WM\_NOTIFY** 訊息至處理函式，以通知程式碼。|  
|[NOTIFY\_HANDLER](../Topic/NOTIFY_HANDLER.md)|將 **WM\_NOTIFY** 訊息至處理函式，以通知程式碼和控制項的識別項。|  
|[NOTIFY\_ID\_HANDLER](../Topic/NOTIFY_ID_HANDLER.md)|將 **WM\_NOTIFY** 訊息至處理函式，根據控制項的識別項。|  
|[NOTIFY\_RANGE\_CODE\_HANDLER](../Topic/NOTIFY_RANGE_CODE_HANDLER.md)|將 **WM\_NOTIFY** 訊息至處理函式，以通知程式碼和控制識別項的一個連續範圍。|  
|[NOTIFY\_RANGE\_HANDLER](../Topic/NOTIFY_RANGE_HANDLER.md)|將 **WM\_NOTIFY** 訊息至處理函式，根據控制識別項的一個連續範圍。|  
|[REFLECT\_NOTIFICATIONS](../Topic/REFLECT_NOTIFICATIONS.md)|反映告知訊息至傳送它們的視窗。|  
|[REFLECTED\_COMMAND\_CODE\_HANDLER](../Topic/REFLECTED_COMMAND_CODE_HANDLER.md)|會將所反映的 **WM\_COMMAND** 訊息至處理函式，以通知程式碼。|  
|[REFLECTED\_COMMAND\_HANDLER](../Topic/REFLECTED_COMMAND_HANDLER.md)|會將所反映的 **WM\_COMMAND** 訊息至處理函式，以通知程式碼和功能表項目、控制項或快速鍵的識別項。|  
|[REFLECTED\_COMMAND\_ID\_HANDLER](../Topic/REFLECTED_COMMAND_ID_HANDLER.md)|會將所反映的 **WM\_COMMAND** 訊息至處理函式，根據功能表項目、控制項或快速鍵的識別項。|  
|[REFLECTED\_COMMAND\_RANGE\_CODE\_HANDLER](../Topic/REFLECTED_COMMAND_RANGE_CODE_HANDLER.md)|會將所反映的 **WM\_COMMAND** 訊息至處理函式，以通知程式碼和控制識別項的一個連續範圍。|  
|[REFLECTED\_COMMAND\_RANGE\_HANDLER](../Topic/REFLECTED_COMMAND_RANGE_HANDLER.md)|會將所反映的 **WM\_COMMAND** 訊息至處理函式，根據控制識別項的一個連續範圍。|  
|[REFLECTED\_NOTIFY\_CODE\_HANDLER](../Topic/REFLECTED_NOTIFY_CODE_HANDLER.md)|會將所反映的 **WM\_NOTIFY** 訊息至處理函式，以通知程式碼。|  
|[REFLECTED\_NOTIFY\_HANDLER](../Topic/REFLECTED_NOTIFY_HANDLER.md)|會將所反映的 **WM\_NOTIFY** 訊息至處理函式，以通知程式碼和控制項的識別項。|  
|[REFLECTED\_NOTIFY\_ID\_HANDLER](../Topic/REFLECTED_NOTIFY_ID_HANDLER.md)|會將所反映的 **WM\_NOTIFY** 訊息至處理函式，根據控制項的識別項。|  
|[REFLECTED\_NOTIFY\_RANGE\_CODE\_HANDLER](../Topic/REFLECTED_NOTIFY_RANGE_CODE_HANDLER.md)|會將所反映的 **WM\_NOTIFY** 訊息至處理函式，以通知程式碼和控制識別項的一個連續範圍。|  
|[REFLECTED\_NOTIFY\_RANGE\_HANDLER](../Topic/REFLECTED_NOTIFY_RANGE_HANDLER.md)|會將所反映的 **WM\_NOTIFY** 訊息至處理函式，根據控制識別項的一個連續範圍。|  
  
## 請參閱  
 [Macros](../../atl/reference/atl-macros.md)