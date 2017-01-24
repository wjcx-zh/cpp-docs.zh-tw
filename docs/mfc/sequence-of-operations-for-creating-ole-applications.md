---
title: "建立 OLE 應用程式的作業順序 | Microsoft Docs"
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
  - "應用程式 [OLE]"
  - "應用程式 [OLE], 建立"
  - "OLE 應用程式 [C++]"
  - "OLE 應用程式 [C++], 建立"
ms.assetid: 84b0f606-36c1-4253-9cea-44427f0074b9
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建立 OLE 應用程式的作業順序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表顯示您的角色和架構的作用在建立連接和內嵌應用程式的 OLE。  這些表示選項可用而非的步驟執行。  
  
### 建立應用程式  
  
|工作|您做|架構做|  
|--------|--------|---------|  
|建立 COM 元件。|執行 MFC 應用程式精靈。  選取 **Full\-server** 或 **Mini\-server** 在 **Compound Document Support** 選項。|框架會產生與 COM 元件功能允許基本架構應用程式。  所有 COM 功能可以傳輸到只有些許的修改現有的應用程式。|  
|從頭開始建立容器應用程式。|執行 MFC 應用程式精靈。  選取 **Compound Document Support** 選項的 **Container** 。  欲使用類別檢視，請至程式碼編輯器。  填入您的 COM 處理函式的程式碼。|框架產生可以插入 COM 元件的基本架構應用程式 \(伺服器\) 應用程式建立的 COM 物件。|  
|從頭開始建立支援 Automation 的應用程式。|執行 MFC 應用程式精靈。  從 \[**進階功能**\] 索引標籤選取 **Automation** 。  使用類別檢視所公開的方法和屬性在您的應用程式對自動化。|框架會產生可供其他應用程式啟動和 Automation 基本架構應用程式。|  
  
## 請參閱  
 [在架構上建置](../mfc/building-on-the-framework.md)   
 [建置 MFC 應用程式的作業順序](../mfc/sequence-of-operations-for-building-mfc-applications.md)   
 [建立 ActiveX 控制項的作業順序](../mfc/sequence-of-operations-for-creating-activex-controls.md)   
 [建立資料庫應用程式的作業順序](../mfc/sequence-of-operations-for-creating-database-applications.md)