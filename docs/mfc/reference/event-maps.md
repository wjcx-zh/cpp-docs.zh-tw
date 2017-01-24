---
title: "事件對應 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.maps"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "事件對應"
ms.assetid: 1ed53aee-bc53-43cd-834a-6fb935c0d29b
caps.latest.revision: 15
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 事件對應
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當控制項要向其容器一些動作 \(由控制項開發人員\) 出現 \(例如一個按鍵、按一下滑鼠或變更控制項的狀態\) 會呼叫引發事件函式。  這個函式會告知控制項容器的一些重要動作傳遞引發相關的事件發生。  
  
 MFC 程式庫提供引發事件最佳化的程式設計模型。  在這個模型中，函式引發特定控制項之事件的「事件對應」來指定。  事件將包含每個事件的巨集。  例如，引發股票 Click 事件的事件的對應如下所示::  
  
 [!code-cpp[NVC_MFCAxCtl#16](../../mfc/reference/codesnippet/CPP/event-maps_1.cpp)]  
  
 **EVENT\_STOCK\_CLICK** 巨集表示控制項都會引發股票 Click 事件偵測到滑鼠點選動作。  如需其他內建事件更詳細的清單，請參閱本文件的 [ActiveX 控制項:事件](../../mfc/mfc-activex-controls-events.md)。  巨集也可以使用自訂事件。  
  
 雖然事件對應巨集很重要，您通常不會直接插入它們。  這是因為，當您使用其關聯之事件引發函式與事件時，屬性視窗會自動在您的原始程式檔建立的事件對應項目。  在您要編輯或加入事件對應項目時，您可以使用屬性視窗。  
  
 若要支援事件對應， MFC 提供下列巨集:  
  
### 事件將宣告和分界  
  
|||  
|-|-|  
|[DECLARE\_EVENT\_MAP](../Topic/DECLARE_EVENT_MAP.md)|宣告事件將會使用類別將事件傳遞至事件引發函式 \(必須在類別宣告\)。|  
|[BEGIN\_EVENT\_MAP](../Topic/BEGIN_EVENT_MAP.md)|啟動事件對應的定義 \(必須使用類別實作\)。|  
|[END\_EVENT\_MAP](../Topic/END_EVENT_MAP.md)|結束事件對應的定義 \(必須使用類別實作\)。|  
  
### 事件對應巨集  
  
|||  
|-|-|  
|[EVENT\_CUSTOM](../Topic/EVENT_CUSTOM.md)|事件引發函式會引發指定的事件的指示。|  
|[EVENT\_CUSTOM\_ID](../Topic/EVENT_CUSTOM_ID.md)|事件引發函式會引發指定的事件的指示，使用指定的分派識別碼 .|  
  
### 訊息對應巨集  
  
|||  
|-|-|  
|[ON\_OLEVERB](../Topic/ON_OLEVERB.md)|表示 OLE 控制項處理的自訂動詞命令。|  
|[ON\_STDOLEVERB](../Topic/ON_STDOLEVERB.md)|覆寫 OLE 控制項的標準動詞命令對應。|  
  
## 請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)