---
title: "加入 ATL 訊息處理常式 | Microsoft Docs"
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
  - "ATL, 訊息處理常式"
  - "ATL, 視窗"
  - "message handlers [C++]"
  - "message handling [C++], ATL message handler"
  - "windows [C++], ATL"
ms.assetid: cdea38a1-0d9b-4f8d-bbd5-b4f063fb3eeb
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 加入 ATL 訊息處理常式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要將訊息處理常式 \(處理 Windows 訊息的成員 \(Member\) 函式\) 加入至控制項，請先選擇在類別檢視中的控制項。  然後 \[**屬性**\] 開啟  視窗中，選取 **訊息** 圖示，然後按一下方塊中的下拉式控制項中的訊息相反。  這會將訊息處理常式的宣告處理常式之控制項的標頭檔 \(Header File\) 和基本架構實作的控制項的 .cpp 檔中。  它也會將訊息對應並加入處理常式的項目。  
  
 加入 ATL 的訊息處理常式類似於將訊息處理常式加入至 MFC 類別。  請參閱 [加入 MFC 訊息處理常式](../mfc/reference/adding-an-mfc-message-handler.md) 以取得詳細資訊。  
  
 下列條件只適用於將 ATL 訊息處理常式:  
  
-   訊息處理常式遵循命名慣例和 MFC 相同。  
  
-   新的訊息對應項目加入到主要訊息對應。  精靈無法辨識替代的訊息對應和繫結。  
  
## 請參閱  
 [Implementing a Window](../atl/implementing-a-window.md)