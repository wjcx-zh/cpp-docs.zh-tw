---
title: "訊息對應巨集 (MFC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.messages"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "區分 Windows 訊息"
  - "訊息對應巨集"
  - "訊息對應範圍"
  - "訊息對應巨集"
  - "訊息對應 [C++], 宣告和區分"
  - "訊息對應 [C++], 巨集"
  - "範圍, 訊息對應"
  - "Windows 訊息 [C++], 宣告"
ms.assetid: 531b15ce-32b5-4ca0-a849-bb519616c731
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 訊息對應巨集 (MFC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要支援訊息對應， MFC 提供下列巨集:  
  
### 訊息對應宣告和分界巨集  
  
|||  
|-|-|  
|[DECLARE\_MESSAGE\_MAP](../Topic/DECLARE_MESSAGE_MAP.md)|宣告的訊息對應會使用類別將訊息傳送至函式 \(必須在類別宣告\)。|  
|[BEGIN\_MESSAGE\_MAP](../Topic/BEGIN_MESSAGE_MAP.md)|啟動訊息對應的定義 \(必須使用類別實作\)。|  
|[END\_MESSAGE\_MAP](../Topic/END_MESSAGE_MAP.md)|結束訊息對應的定義 \(必須使用類別實作\)。|  
  
### 訊息對應巨集  
  
|||  
|-|-|  
|[ON\_COMMAND](../Topic/ON_COMMAND.md)|函式會處理指定的命令訊息的指示。|  
|[ON\_CONTROL](../Topic/ON_CONTROL.md)|函式會處理指定的控制項告知訊息的指示。|  
|[ON\_MESSAGE](../Topic/ON_MESSAGE.md)|函式會處理使用者定義訊息的指示。|  
|[ON\_OLECMD](../Topic/ON_OLECMD.md)|函式會處理來自 DocObject 或其容器的功能表命令的指示。|  
|[ON\_REGISTERED\_MESSAGE](../Topic/ON_REGISTERED_MESSAGE.md)|函式會處理註冊使用者定義訊息的指示。|  
|[ON\_REGISTERED\_THREAD\_MESSAGE](../Topic/ON_REGISTERED_THREAD_MESSAGE.md)|函式會處理已註冊之使用者定義的訊息的指示，當您有一個 `CWinThread` 類別。|  
|[ON\_THREAD\_MESSAGE](../Topic/ON_THREAD_MESSAGE.md)|函式會處理使用者定義的訊息的指示，當您有一個 `CWinThread` 類別。|  
|[ON\_UPDATE\_COMMAND\_UI](../Topic/ON_UPDATE_COMMAND_UI.md)|函式會處理指定的使用者介面更新命令訊息的指示。|  
  
### 訊息對應範圍巨集  
  
|||  
|-|-|  
|[ON\_COMMAND\_RANGE](../Topic/ON_COMMAND_RANGE.md)|函式處理命令 ID 的範圍的指示在前兩個參數指定給巨集。|  
|[ON\_UPDATE\_COMMAND\_UI\_RANGE](../Topic/ON_UPDATE_COMMAND_UI_RANGE.md)|更新處理常式處理命令 ID 的範圍的指示在前兩個參數指定給巨集。|  
|[ON\_CONTROL\_RANGE](../Topic/ON_CONTROL_RANGE.md)|函式會處理來自控制項 ID 的範圍的通知表示在第二和第三個參數指定給巨集。  第一個參數是控制項通知訊息，例如 **BN\_CLICKED**。|  
  
 如需訊息對應的詳細資訊，訊息對應宣告和分界巨集和訊息對應巨集，請參閱 [訊息對應](../../mfc/reference/message-maps-mfc.md) 和 [訊息處理和對應的主題](../../mfc/message-handling-and-mapping.md)。  如需訊息對應範圍的詳細資訊，請參閱 [訊息對應範圍的處理常式。](../../mfc/handlers-for-message-map-ranges.md)。  
  
## 請參閱  
 [訊息對應](../../mfc/reference/message-maps-mfc.md)