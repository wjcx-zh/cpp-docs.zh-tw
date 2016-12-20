---
title: "衍生訊息對應 | Microsoft Docs"
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
  - "衍生訊息對應"
  - "訊息處理, 衍生訊息處理常式"
  - "訊息對應, 衍生"
  - "訊息, 傳送"
ms.assetid: 21829556-6e64-40c3-8279-fed85d99de77
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 衍生訊息對應
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在訊息處理期間，檢查類別本身的訊息對應不是訊息對應劇本結尾。  會產生類別，則為 `CMyView` \(衍生自 `CView`\) 沒有訊息的符合項目?  
  
 請記住， `CView`，`CMyView`基底類別， 而後者又衍生自`CWnd`。  以 `CMyView` *為*`CView` 且 *為*`CWnd`。  這些類別都有自己的訊息對應。  這個圖形檢視階層架構，顯示類別的階層關聯性，但請記住， `CMyView` 物件會有三個類別特性的單一物件。  
  
 ![檢視的階層架構](../mfc/media/vc38621.png "vc38621")  
檢視階層架構  
  
 因此，如果訊息在類別 `CMyView` 訊息對應無法符合，架構也搜尋其直接基底類別的訊息對應。  在訊息對應的開始 `BEGIN_MESSAGE_MAP` 巨集指定兩個類別名稱做為其引數:  
  
 [!code-cpp[NVC_MFCMessageHandling#2](../mfc/codesnippet/CPP/derived-message-maps_1.cpp)]  
  
 第一個引數命名訊息對應所屬的類別。  第二個引數提供連接直接基底類別 \(例如 `CView` \)，因此架構也可以搜尋其訊息對應。  
  
 在基底類別所提供的訊息處理常式由衍生類別繼承。  這非常類似於一般虛擬成員函式，而不需要讓所有處理常式虛擬成員函式。  
  
 如果處理常式在找不到任何基底類別訊息對應，預設處理訊息執行。  如果訊息是命令，架構會路由到下一個命令目標。  如果是標準 Windows 訊息，訊息傳遞至適當的預設視窗程序。  
  
 若要加速訊息對應符合，架構會快取在可能最符合的，它再次收到相同的訊息。  這個的結果是相當有效率地處理未處理訊息的架構。  訊息對應比使用虛擬函式的實作更為空間有效。  
  
## 請參閱  
 [架構如何搜尋訊息對應](../mfc/how-the-framework-searches-message-maps.md)