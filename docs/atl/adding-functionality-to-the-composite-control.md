---
title: "Adding Functionality to the Composite Control | Microsoft Docs"
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
  - "ActiveX 控制項 [C++], 事件"
  - "複合控制項, 處理事件"
  - "event handlers [C++], ActiveX 控制項"
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Adding Functionality to the Composite Control
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一旦插入所有必要的控制項到複合控制項，下一個步驟包括加入新功能。  這個新功能通常可分為兩類:  
  
-   支援額外的介面及自訂的複合控制項的行為和此外，特定的功能。  
  
-   處理從內含的 ActiveX 控制項 \(或\) 控制項的事件。  
  
 如果目的和範圍本文，本節其餘部分分別著重於處理來自 ActiveX 控制項的事件。  
  
> [!NOTE]
>  如果您需要處理視窗控制項的訊息，請參閱 [實作視窗](../atl/implementing-a-window.md) 有關訊息處理 ATL 中的詳細資訊。  
  
 在插入 ActiveX 控制項之後在對話方塊資源中，以滑鼠右鍵按一下控制項並按一下 \[**加入事件處理常式**\]。  選取您要處理並按一下 **Add and Edit**的事件。  事件處理常式程式碼將會加入至控制項的 .h 檔案。  
  
 ActiveX 控制項的連接點包含在複合控制項透過呼叫會自動連接和中斷連接至 [CComCompositeControl::AdviseSinkMap](../Topic/CComCompositeControl::AdviseSinkMap.md)。  
  
## 請參閱  
 [複合控制項基本概念](../atl/atl-composite-control-fundamentals.md)