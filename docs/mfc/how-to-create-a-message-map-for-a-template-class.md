---
title: "如何：建立樣板類別的訊息對應 | Microsoft Docs"
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
  - "訊息對應, 樣板類別"
  - "樣板類別, 建立訊息對應"
ms.assetid: 4e7e24f8-06df-4b46-82aa-7435c8650de3
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 如何：建立樣板類別的訊息對應
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 MFC 的訊息對應會提供有效的方法會將 Windows 訊息至適當的 C\+\+ 物件執行個體。  MFC 訊息對應目標的範例包括應用程式類別、文件和檢視類別，控制項類別，依此類推。  
  
 傳統 MFC 訊息對應宣告使用 [BEGIN\_MESSAGE\_MAP](../Topic/BEGIN_MESSAGE_MAP.md) 巨集宣告的訊息對應的開始，每個訊息處理常式類別方法的巨集輸入和 [END\_MESSAGE\_MAP](../Topic/END_MESSAGE_MAP.md) 巨集最後宣告的訊息對應的結尾。  
  
 使用 [BEGIN\_MESSAGE\_MAP](../Topic/BEGIN_MESSAGE_MAP.md) 巨集出現的限制，當它與包含樣板引數的類別結合使用。  當使用樣板類別，這個巨集就會造成編譯時期錯誤遺漏的範本參數在巨集展開期間。  [BEGIN\_TEMPLATE\_MESSAGE\_MAP](../Topic/BEGIN_TEMPLATE_MESSAGE_MAP.md) 巨集的設計是包含單一樣板引數的類別宣告自己的訊息對應。  
  
## 範例  
 考慮 MFC [CListBox](../mfc/reference/clistbox-class.md) 類別會擴充提供同步處理以外部資料來源的範例。  **CSyncListBox** 類別的宣告方式如下：  
  
 [!code-cpp[NVC_MFC_CListBox#42](../mfc/codesnippet/CPP/how-to-create-a-message-map-for-a-template-class_1.h)]  
  
 **CSyncListBox** 類別在描述資料來源它會同步處理的單一型別樣板。  它也宣告加入類別的訊息對應的三個方法: **OnPaint**和 **OnDestroy**和 **OnSynchronize**。  **OnSynchronize** 方法執行如下:  
  
 [!code-cpp[NVC_MFC_CListBox#43](../mfc/codesnippet/CPP/how-to-create-a-message-map-for-a-template-class_2.cpp)]  
  
 上述實作在執行 **GetCount** 方法，例如 **CArray**， **CList**的任何類別型別 **CMap**和 **CSyncListBox** 允許類別特製化。  **StringizeElement** 是函式樣板函式原型由下列:  
  
 [!code-cpp[NVC_MFC_CListBox#44](../mfc/codesnippet/CPP/how-to-create-a-message-map-for-a-template-class_3.cpp)]  
  
 通常，這個類別的訊息對應會定義如下:  
  
 `BEGIN_MESSAGE_MAP(CSyncListBox, CListBox)`  
  
 `ON_WM_PAINT()`  
  
 `ON_WM_DESTROY()`  
  
 `ON_MESSAGE(LBN_SYNCHRONIZE, OnSynchronize)`  
  
 `END_MESSAGE_MAP()`  
  
 其中 **LBN\_SYNCHRONIZE** 是應用程式定義的自訂使用者訊息，例如:  
  
 [!code-cpp[NVC_MFC_CListBox#45](../mfc/codesnippet/CPP/how-to-create-a-message-map-for-a-template-class_4.cpp)]  
  
 上面巨集對應不會進行編譯，因為在巨集展開期間， **CSyncListBox** 類別的樣板規格遺漏這類的事實。  **BEGIN\_TEMPLATE\_MESSAGE\_MAP** 巨集以合併指定的樣板參數解析至展開的巨集對應。  這個類別的訊息對應會為:  
  
 [!code-cpp[NVC_MFC_CListBox#46](../mfc/codesnippet/CPP/how-to-create-a-message-map-for-a-template-class_5.cpp)]  
  
 使用 **CStringList** 物件，下列示範 **CSyncListBox** 類別的範例使用方式:  
  
 [!code-cpp[NVC_MFC_CListBox#47](../mfc/codesnippet/CPP/how-to-create-a-message-map-for-a-template-class_6.cpp)]  
  
 若要完成測試，必須特製化函式 **StringizeElement** 和 **CStringList** 類別一起使用:  
  
 [!code-cpp[NVC_MFC_CListBox#48](../mfc/codesnippet/CPP/how-to-create-a-message-map-for-a-template-class_7.cpp)]  
  
## 請參閱  
 [BEGIN\_TEMPLATE\_MESSAGE\_MAP](../Topic/BEGIN_TEMPLATE_MESSAGE_MAP.md)   
 [訊息處理和對應](../mfc/message-handling-and-mapping.md)