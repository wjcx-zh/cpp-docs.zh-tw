---
title: "CReBar 和 CReBarCtrl 比較 | Microsoft Docs"
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
  - "CReBar"
  - "CReBarCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CReBar 類別, 和 CReBarCtrl 比較"
  - "GetReBarCtrl 類別"
  - "Rebar 控制項, CReBarCtrl 類別"
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CReBar 和 CReBarCtrl 比較
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 提供兩個類別給建立的筋:\(包裝 Windows 通用控制項 API\) 的 [CReBar](../mfc/reference/crebar-class.md) 和 [CReBarCtrl](../mfc/reference/crebarctrl-class.md) 。  **CReBar** 提供所有公用 Rebar 控制項的功能，因此，它處理許多必要的通用控制項設定和結構中。  
  
 如果您不想要整合 Rebar MFC 架構，`CReBarCtrl` 是 Win32 Rebar 控制項的包裝函式類別，因此可能會更容易實作。  如果您計劃使用 `CReBarCtrl` 和整合 Rebar MFC 架構，您必須注意其他傳達 Rebar 控制項作業加入至 MFC。  這個通訊並不困難;不過，它是不需要的其他工作，請使用 **CReBar**時。  
  
 Visual C\+\+ 提供兩種利用 Rebar 通用控制項。  
  
-   使用 **CReBar**，建立 Rebar，然後呼叫 [CReBar::GetReBarCtrl](../Topic/CReBar::GetReBarCtrl.md) 取得 `CReBarCtrl` 成員函式的存取。  
  
    > [!NOTE]
    >  `CReBar::GetReBarCtrl` 轉型為 Rebar 物件的 **this** 指標的內嵌成員函式。  這表示，在執行階段，函式呼叫沒有額外負荷。  
  
-   使用 [CReBarCtrl](../mfc/reference/crebarctrl-class.md) 建構函式，建立 Rebar 群組列。  
  
 這些方法可讓您對 Rebar 控制項的成員函式的存取。  當您呼叫 `CReBar::GetReBarCtrl`時，會傳回 `CReBarCtrl` 物件的參考，因此您可以使用任一組成員函式。  使用 **CReBar**，請參閱 [CReBar](../mfc/reference/crebar-class.md) 與用來建構和建立 Rebar 的資訊。  
  
## 請參閱  
 [使用 CReBarCtrl](../mfc/using-crebarctrl.md)   
 [控制項](../mfc/controls-mfc.md)