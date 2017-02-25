---
title: "伺服器：實作就地編輯框架視窗 | Microsoft Docs"
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
  - "框架視窗, 實作"
  - "框架視窗, in-place"
  - "就地編輯框架視窗"
  - "OLE 伺服器應用程式, 框架視窗"
  - "伺服器, 就地編輯框架視窗"
ms.assetid: 09bde4d8-15e2-4fba-8d14-9b954d926b92
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 伺服器：實作就地編輯框架視窗
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明所必須實作自己的視覺化編輯伺服器應用程式的就地框架視窗，如果不使用應用程式精靈來建立您的伺服器應用程式。  在遵循本文概述的程序位置，您可以使用應用程式精靈產生的應用程式或範例的現有就地框架視窗類別隨 Visual C\+\+。  
  
#### 宣告就地框架視窗類別  
  
1.  從 `COleIPFrameWnd`取得就地框架視窗類別。  
  
    -   使用 `DECLARE_DYNCREATE` 巨集在類別的標頭檔。  
  
    -   使用 `IMPLEMENT_DYNCREATE` 巨集在類別中實作 \(.cpp\) 檔。  這可讓此類別物件由架構建立。  
  
2.  宣告框架視窗類別的一個 `COleResizeBar` 成員。  如果您要支援就地調整在伺服器應用程式，這是必要的。  
  
     宣告 `OnCreate` 訊息處理常式 \(使用 \[**屬性**\] 視窗\)，如果您定義了，則並呼叫您的 `COleResizeBar` 成員的 **Create** 。  
  
3.  如果您有工具列，請宣告框架視窗類別的一個 `CToolBar` 成員。  
  
     當伺服器作用中的時，請覆寫 `OnCreateControlBars` 成員函式來建立工具列。  例如：  
  
     [!code-cpp[NVC_MFCOleServer#1](../mfc/codesnippet/CPP/servers-implementing-in-place-frame-windows_1.cpp)]  
  
     在步驟 5，請參閱如需此程式碼的討論。  
  
4.  這包括就地框架視窗類別的標頭檔中的主要 .cpp 檔案。  
  
5.  在您的應用程式類別的 `InitInstance` ，請呼叫文件樣板物件的 `SetServerInfo` 函式指定用來開啟和就地編輯和就地框架視窗的資源。  
  
 函式呼叫繪製於 **if** 陳述式建立從伺服器所提供的資源的工具列。  此時，工具列是容器的視窗階層架構的一部分。  由於這個工具列衍生自 `CToolBar`，它會透過其訊息給它的擁有人，容器應用程式框架視窗，除非您變更擁有者。  因此對 `SetOwner` 的呼叫是必要的。  這個呼叫變更命令傳送是伺服器的就地框架視窗，造成訊息傳遞至伺服器。  這可讓伺服器回應所提供之工具列的作業。  
  
 工具列點陣圖的 ID 應該與在您的伺服器應用程式定義的其他就地資源。  請參閱 [功能表和資源:伺服器加入](../mfc/menus-and-resources-server-additions.md) 以取得詳細資訊。  
  
 在 *類別庫參考 \(*如需詳細資訊，請參閱 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)、 [COleResizeBar](../mfc/reference/coleresizebar-class.md)和 [CDocTemplate::SetServerInfo](../Topic/CDocTemplate::SetServerInfo.md) 。  
  
## 請參閱  
 [伺服器](../mfc/servers.md)   
 [伺服器：實作伺服器](../mfc/servers-implementing-a-server.md)   
 [伺服器：實作伺服器文件](../mfc/servers-implementing-server-documents.md)   
 [伺服器：伺服器項目](../mfc/servers-server-items.md)