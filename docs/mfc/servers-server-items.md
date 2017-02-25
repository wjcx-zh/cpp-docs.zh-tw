---
title: "伺服器：伺服器項目 | Microsoft Docs"
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
  - "架構 [C++], 伺服器項目"
  - "OLE 伺服器應用程式, 伺服器項目"
  - "伺服器項目"
  - "伺服器項目, 實作"
  - "伺服器 [C++], 伺服器項目"
ms.assetid: 28ba81a1-726a-4728-a52d-68bc7efd5a3c
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 伺服器：伺服器項目
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當容器啟動伺服器時，讓使用者可以編輯內嵌或連結的 OLE 項目，伺服器應用程式建立「server」項目。伺服器項目，類別是衍生自 `COleServerItem`的物件，提供伺服器資料和容器應用程式之間的介面。  
  
 `COleServerItem` 類別通常會定義由 OLE 呼叫的數個可覆寫成員函式，以回應從容器的要求。  伺服器項目可能代表一部分的伺服器文件或整個文件。  當 OLE 項目容器在文件中嵌入，伺服器項目代表整個伺服器文件。  當 OLE 項目連結時，伺服器項目可能表示伺服器文件或整份文件的部分，依賴此連結是否為組件或對整體。  
  
 在 [HIERSVR](../top/visual-cpp-samples.md) 範例中，例如，伺服器項目類別， **CServerItem**，不是指向類別 **CServerNode**的物件的成員。  **CServerNode** 物件是在 HIERSVR 應用程式檔案的一個節點，是樹狀目錄。  當 **CServerNode** 物件是根節點時， **CServerItem** 物件代表整份文件。  當 **CServerNode** 物件是子節點時， **CServerItem** 物件表示文件中的章節。  如需這個函式的範例，請參閱 [HIERSVR](../top/visual-cpp-samples.md)範例。  
  
##  <a name="_core_implementing_server_items"></a> 實作伺服器項目  
 如果您使用應用程式精靈會產生「應用程式的起始」程式碼，則起始必須包括伺服器項目的程式碼是從 OLE 選項頁選取其中一個伺服器選項的所有。  如果您將伺服器項目加入至現有的應用程式，請執行下列步驟:  
  
#### 實作伺服器項目  
  
1.  從 `COleServerItem` 衍生類別。  
  
2.  在衍生類別中，覆寫 `OnDraw` 成員函式。  
  
     這個架構呼叫 `OnDraw` 呈現 OLE 項目至中繼檔。  容器應用程式使用此中繼檔呈現項目。  您的應用程式的檢視類別也有一個 `OnDraw` 成員函式，用來呈現項目，當伺服器應用程式為作用中時。  
  
3.  實作 `OnGetEmbeddedItem` 覆寫您的伺服器資料類別的。  如需詳細資訊，請參閱本文 [伺服器:實作伺服器資料](../mfc/servers-implementing-server-documents.md) 和 MFC OLE [HIERSVR](../top/visual-cpp-samples.md)範例。  
  
4.  實作您的伺服器項目類別的 `OnGetExtent` 成員函式。  架構會呼叫這個函式會擷取項目的大小。  預設實作不做任何動作。  
  
##  <a name="_core_a_tip_for_server.2d.item_architecture"></a> 伺服器項目的架構提示  
 在 [實作伺服器項目](#_core_implementing_server_items)中的指示，伺服器應用程式必須能夠呈現項目在伺服器上檢視和在容器應用程式使用的中繼檔。  在 MFC 程式庫的應用程式架構中，檢視類別的 `OnDraw` 成員函式呈現項目，會在編譯期間 \(請參閱*類別庫參考*[中的CView::OnDraw](../Topic/CView::OnDraw.md) \)。  伺服器項目的 `OnDraw` 呈現項目至中繼檔在其他所有情況下 \(請參閱 [COleServerItem::OnDraw](../Topic/COleServerItem::OnDraw.md)\)。  
  
 您可以撰寫 Helper 函式在您的伺服器資料類別和呼叫它們避免程式碼的複製 `OnDraw` 函式在您的檢視和伺服器項目類別。  MFC OLE [HIERSVR](../top/visual-cpp-samples.md) 範例使用這個策略:函式 **CServerView::OnDraw** 和 **CServerItem::OnDraw** 都呼叫 **CServerDoc::DrawTree** 呈現項目。  
  
 因為它們在不同的狀況下，繪製檢視和項目都具有 `OnDraw` 成員函式。  檢視中必須考慮到這種因素像縮放，選取大小和範圍、裁剪和使用者介面項目 \(例如捲軸\)。  伺服器項目，另一方面一律會繪製整個 OLE 物件。  
  
 在 *類別庫參考 \(*如需詳細資訊，請參閱 [CView::OnDraw](../Topic/CView::OnDraw.md)、 [COleServerItem](../mfc/reference/coleserveritem-class.md)、 [COleServerItem::OnDraw](../Topic/COleServerItem::OnDraw.md)和 [COleServerDoc::OnGetEmbeddedItem](../Topic/COleServerDoc::OnGetEmbeddedItem.md) 。  
  
## 請參閱  
 [伺服器](../mfc/servers.md)