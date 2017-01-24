---
title: "如何：從 MFC 應用程式載入功能區應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "功能區資源, 載入"
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：從 MFC 應用程式載入功能區應用程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要使用功能區資源在應用程式中，修改應用程式載入功能區資源。  
  
### 載入功能區資源  
  
1.  宣告 `Ribbon Control` 物件，在 `CMainFrame` 類別。  
  
    ```  
    CMFCRibbonBar m_wndRibbonBar;   
    ```  
  
2.  在 `CMainFrame::OnCreate`中，建立並初始化功能區控制項。  
  
    ```  
    if (!m_wndRibbonBar.Create (this))  
    {  
        return -1;  
    }  
  
    if (!m_wndRibbonBar.LoadFromResource(IDR_RIBBON))  
    {  
        return -1;  
    }  
    ```  
  
## 請參閱  
 [功能區設計工具 \(MFC\)](../mfc/ribbon-designer-mfc.md)