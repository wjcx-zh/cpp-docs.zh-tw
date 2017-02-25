---
title: "Message Maps (ATL) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, 訊息處理常式"
  - "message maps, ATL"
ms.assetid: 9e100400-65c7-4a85-8857-4e6cb6dd7340
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Message Maps (ATL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

訊息對應關聯處理函式和特定訊息、命令或通知。  使用 ATL 的 [訊息對應巨集](../atl/reference/message-map-macros-atl.md)，您可以在視窗中指定訊息對應。  在 `CWindowImpl`、 `CDialogImpl`和 `CContainedWindowT` 的視窗程序導向到視窗的訊息傳送至訊息對應。  
  
 [訊息處理常式函式](../atl/message-handler-functions.md) 接受型別 `BOOL_&`的其他引數。  這個引數表示訊息是否處理，根據預設，並且設定為 `TRUE` 。  處理函式可設定引數傳遞至 `FALSE` 指出它未處理訊息。  在這個案例中， ATL 會繼續搜尋處理函式進一步在訊息對應。  將設定為 `FALSE`的這個引數，您可以先執行某些動作以回應訊息會允許預設處理或另一個處理常式函式至處理訊息的。  
  
## 繫結至的訊息對應  
 ATL 也可讓您繫結訊息對應，指示訊息處理到另一個類別中定義的訊息對應。  例如，您可以實作處理不同類別的通用訊息供繫結使用所有的視窗提供一致的行為寫入該類別。  您可以繫結至基底類別或對類別的資料成員。  
  
 ATL 也支援動態繫結，讓您可以繫結至另一個物件的訊息對應於執行階段。  若要實作動態繫結，您必須從 [CDynamicChain](../atl/reference/cdynamicchain-class.md)衍生您的類別。  然後在您宣告的訊息對應的 [CHAIN\_MSG\_MAP\_DYNAMIC](../Topic/CHAIN_MSG_MAP_DYNAMIC.md) 巨集。  `CHAIN_MSG_MAP_DYNAMIC` 要求識別物件和訊息對應要繫結的唯一數字。  您必須透過呼叫來定義這個唯一的值加入至 `CDynamicChain::SetChainEntry`。  
  
 您可以繫結至宣告的訊息對應的任何類別，，假設類別 [CMessageMap](../atl/reference/cmessagemap-class.md)從衍生。  `CMessageMap` 可讓物件將其訊息對應於其他物件。  請注意 `CWindowImpl` 從 `CMessageMap`已經取得。  
  
## 替代的訊息對應  
 最後， ATL 支援替代的訊息對應，宣告 [ALT\_MSG\_MAP](../Topic/ALT_MSG_MAP.md) 巨集。  每一個替代的訊息對應是由唯一號碼來識別，傳遞至 `ALT_MSG_MAP`。  使用替代的訊息對應，管理多個視窗訊息在對應的。  請注意，根據預設， `CWindowImpl` 不使用替代的訊息對應。  將這項支援，以覆寫您的 `CWindowImpl`的 `WindowProc` 方法衍生類別和呼叫的訊息對應識別項的 `ProcessWindowMessage` 。  
  
## 請參閱  
 [Implementing a Window](../atl/implementing-a-window.md)