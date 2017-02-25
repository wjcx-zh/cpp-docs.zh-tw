---
title: "MFC ActiveX 控制項：事件 | Microsoft Docs"
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
  - "COleControl 類別, 事件的處理"
  - "容器事件"
  - "自訂事件, 加入至 ActiveX 控制項"
  - "事件 [C++], ActiveX 控制項"
  - "事件 [C++], 對應"
  - "對應, 事件"
  - "MFC ActiveX 控制項, 事件"
  - "告知 [C++], 將事件告知容器"
  - "OLE 事件"
  - "內建事件"
ms.assetid: e1e57e0c-206b-4923-a0b5-682c26564f74
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# MFC ActiveX 控制項：事件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ActiveX 控制項通知事情發生在控制項的容器使用的事件。  事件包含的常見範例在控制項中按一下控制項，使用鍵盤輸入的資料，以及變更。  當這些動作發生時，控制項引發事件警告容器。  
  
 事件也稱為訊息。  
  
 MFC 支援兩種事件:內建和自訂。  內建事件會自動把 [COleControl](../mfc/reference/colecontrol-class.md) 處理類別的事件。  如需內建事件的完整清單，請參閱本文件的 [MFC ActiveX 控制項:將內建事件](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)。  當該控制項的特定動作發生時，自訂事件的控制項告知容器。  有些範例是一個變更某個視窗訊息的控制項或應用程式的內部狀態上。  
  
 若要適當地引發控制項的事件，您的控制項類別必須將控制項的每個事件加入應該呼叫成員函式，在相關事件發生時。  這個對應機制 \(稱為事件對應\) 集中事件的相關資訊並讓 Visual Studio 輕鬆存取和操作控制項的事件。  這個事件將由下列巨集來宣告，位於標頭檔 \(。H\) 控制項類別宣告的檔案:  
  
 [!code-cpp[NVC_MFC_AxUI#2](../mfc/codesnippet/CPP/mfc-activex-controls-events_1.h)]  
  
 在事件將宣告之後，在控制項中實作 \(.CPP\) 檔案必須加以定義。  下列程式碼會定義事件對應，讓控制項引發特定事件:  
  
 [!code-cpp[NVC_MFC_AxUI#3](../mfc/codesnippet/CPP/mfc-activex-controls-events_2.cpp)]  
[!code-cpp[NVC_MFC_AxUI#4](../mfc/codesnippet/CPP/mfc-activex-controls-events_3.cpp)]  
  
 如果您使用 MFC ActiveX 控制項精靈建立專案，則會自動將下列程式碼行。  如果您不使用 MFC ActiveX 控制項精靈，您必須手動將這些行。  
  
 類別檢視中，您可以將您定義類別支援的內建事件 `COleControl` 或自訂事件。  對於每個新的事件，類別檢視會自動將適當的項目加入至控制項的事件對應和控制項的 .IDL 檔案。  
  
 其他兩個文章詳細討論事件:  
  
-   [MFC ActiveX 控制項:將內建事件](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)  
  
-   [MFC ActiveX 控制項:將自訂事件](../mfc/mfc-activex-controls-adding-custom-events.md)  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控制項：方法](../mfc/mfc-activex-controls-methods.md)   
 [COleControl Class](../mfc/reference/colecontrol-class.md)