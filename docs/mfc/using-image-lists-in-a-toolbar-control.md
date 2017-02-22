---
title: "在工具列控制項中使用影像清單 | Microsoft Docs"
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
  - "CToolBarCtrl 類別, 影像清單"
  - "影像清單 [C++], 工具列控制項"
  - "工具列控制項 [MFC], 影像"
ms.assetid: ccbe8df4-4ed9-4b54-bb93-9a1dcb3b97eb
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 在工具列控制項中使用影像清單
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

根據預設，按鈕使用的影像在工具列控制項儲存為單一點陣圖。  不過，您可以在一組也可以儲存按鈕影像的影像清單。  工具列控制項物件可以使用三個不同影像清單:  
  
-   可讓影像清單包含目前啟用的工具列按鈕的影像。  
  
-   停用影像清單中目前停用的工具列按鈕的影像。  
  
-   反白顯示的影像清單包含目前反白顯示的工具列按鈕的影像。  這個影像清單，只有在工具列使用 **TBSTYLE\_FLAT** 樣式時，使用。  
  
 當您讓它們與 `CToolBarCtrl` 物件時，工具列控制項使用這些影像清單。  此關聯是透過呼叫 [CToolBarCtrl::SetImageList](../Topic/CToolBarCtrl::SetImageList.md)、 [SetDisabledImageList](../Topic/CToolBarCtrl::SetDisabledImageList.md)和 [SetHotImageList](../Topic/CToolBarCtrl::SetHotImageList.md)的呼叫完成。  
  
 根據預設， MFC 使用 `CToolBar` 類別來實作 MFC 應用程式工具列。  不過， `GetToolBarCtrl` 成員函式來擷取內嵌的 `CToolBarCtrl` 物件。  使用傳回的物件，您可以呼叫 `CToolBarCtrl` 成員函式。  
  
 下列範例將允許 \(`m_ToolBarImages`\) 和停用 \(`m_ToolBarDisabledImages`\) 影像清單示範這項技術套用至 `CToolBarCtrl` 物件 \(`m_ToolBarCtrl`\)。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#35](../mfc/codesnippet/CPP/using-image-lists-in-a-toolbar-control_1.cpp)]  
  
> [!NOTE]
>  工具列物件使用的影像清單必須是永久目標。  因此，它們通常是 MFC 類別的資料成員;在此範例中，主框架視窗類別。  
  
 一旦影像清單與 `CToolBarCtrl` 物件相關聯，架構會自動顯示適當的按鈕影像。  
  
## 請參閱  
 [使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [控制項](../mfc/controls-mfc.md)