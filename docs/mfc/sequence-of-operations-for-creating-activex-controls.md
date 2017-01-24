---
title: "建立 ActiveX 控制項的作業順序 | Microsoft Docs"
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
  - "ActiveX 控制項 [C++], 建立"
  - "MFC ActiveX 控制項 [C++], 建立"
  - "OLE 控制項 [C++], MFC"
  - "序列 [C++]"
  - "序列 [C++], 建立 ActiveX 控制項的"
ms.assetid: 7d868c53-a0af-4ef6-a89c-e1c03c583a53
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建立 ActiveX 控制項的作業順序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表顯示您的角色和架構的作用在建立 ActiveX 控制項 \(先前稱為 OLE automation 控制項\)。  
  
### 建立 ActiveX 控制項  
  
|工作|您做|架構做|  
|--------|--------|---------|  
|建立 ActiveX 控制項框架。|執行 MFC ActiveX 控制項精靈來建立您的控制項。  指定要在索引標籤頁要的選項。  選項是在專案，允許，子類別化和一個方塊方法包含控制項的型別和名稱。|MFC ActiveX 控制項精靈來建立 ActiveX 控制項的檔案與基本功能，包含應用程式的原始程式檔 \(Source File\)、控制項和屬性頁或網頁;資源檔;專案檔;另一個，所有適合您的規格。|  
|查看控制項和 ActiveX 控制項精靈提供，而不加入您的程式碼行。|建立 ActiveX 控制項並測試它與 Internet Explorer 或 [TSTCON 範例](../top/visual-cpp-samples.md)。|執行控制項可以調整大小和移動。  它也有可以叫用的 **About Box** 方法 \(如果選取\)。|  
|實作控制項的方法和屬性。|將成員函式提供公開介面實作您的控制項特定的方法和屬性指定控制項資料。  在決定時，加入成員變數來保存資料結構和使用事件處理常式引發事件。|框架已經定義對應支援控制項的事件，屬性和方法，讓您專注於屬性和方法如何執行。  預設屬性頁可檢視，並提供關於對話方塊方法的預設值。|  
|建置控制項的屬性頁或頁面。|使用 Visual C\+\+ 資源編輯器視覺化編輯控制項的屬性頁介面:<br /><br /> -   建立額外的屬性頁。<br />-   建立及編輯點陣圖、圖示和游標。<br /><br /> 您也可以測試在對話方塊編輯器的屬性頁。|MFC 應用程式精靈建立的預設資源檔提供您所需的許多資源。  Visual C\+\+ 可讓您輕鬆和視覺化編輯現有的資源並加入新的資源。|  
|測試控制項的事件、方法和屬性。|重建控制項並使用測試容器中測試您的處理常式能夠正確地運作。|您可以叫用控制項的方法，並透過屬性頁操作其屬性以測試容器連接或。  此外，請使用控制項和通知給追蹤引發之測試容器接收由控制項的容器。|  
  
## 請參閱  
 [在架構上建置](../mfc/building-on-the-framework.md)   
 [建置 MFC 應用程式的作業順序](../mfc/sequence-of-operations-for-building-mfc-applications.md)   
 [建立 OLE 應用程式的作業順序](../mfc/sequence-of-operations-for-creating-ole-applications.md)   
 [建立資料庫應用程式的作業順序](../mfc/sequence-of-operations-for-creating-database-applications.md)