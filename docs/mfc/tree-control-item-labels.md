---
title: "樹狀目錄控制項目標籤 | Microsoft Docs"
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
  - "CTreeCtrl 類別, 項目標籤"
  - "項目標籤"
  - "項目標籤, 樹狀目錄控制項"
  - "標籤, CTreeCtrl 項目"
  - "樹狀目錄控制項, 項目標籤"
ms.assetid: fe834107-1a25-4280-aced-774c11565805
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 樹狀目錄控制項目標籤
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您通常會指定項目的標籤文字，將項目加入至樹狀目錄控制項 \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\)。  `InsertItem` 成員函式可以定義項目的屬性的 [TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456) 結構，其中包含標籤文字的字串。  `InsertItem` 不可以呼叫具有參數的各種組合的數個多載。  
  
 樹狀目錄控制項配置中的每一項目記憶體;項目標籤的文字會佔用這個記憶體的一個重要的部分。  如果您的應用程式保留字串的複本在樹狀目錄控制項，您可以指定 **LPSTR\_TEXTCALLBACK** 值在 `TV_ITEM` 的 **pszText** 成員或 `lpszItem` 參數來減少控制項的記憶體需求而不是傳遞實際字串對樹狀目錄控制項。  使用 **LPSTR\_TEXTCALLBACK** 造成樹狀目錄控制項從應用程式擷取項目的標籤文字，當項目需要重新繪製。  若要擷取文字，樹狀目錄控制項傳送 [TVN\_GETDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773518) 通知訊息，包括 [NMTVDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773418) 結構的位址。  您必須設定包含結構的適當成員回應。  
  
 樹狀目錄控制項使用從建立樹狀控制流程的堆積配置的記憶體。  項目的最大數目樹狀控制項根據數量堆積中的可用記憶體。  每個項目都需要 64 個位元組。  
  
## 請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)