---
title: "如何：在您的程式碼中實作追蹤 | Microsoft Docs"
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
  - "CRectTracker 類別, 實作追蹤器"
ms.assetid: baaeca2c-5114-485f-bf58-8807db1bc973
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：在您的程式碼中實作追蹤
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要追蹤 OLE 項目，您必須處理特定事件與項目相關，例如按一下項目或更新文件的檢視。  在所有情況下，宣告暫存 [CRectTracker](../mfc/reference/crecttracker-class.md) 物件並透過此物件操作項目即可。  
  
 當使用者選取項目或插入與功能表命令物件時，您必須使用追蹤以適當樣式表示 OLE 項目的狀態。  下表列出 OCLIENT 範例使用慣例。  如需這些模式的詳細資訊，請參閱 `CRectTracker`。  
  
### 容器 OLE 項目的樣式和狀態。  
  
|顯示的樣式|OLE 項目狀態|  
|-----------|--------------|  
|點狀框線|項目連結|  
|實心框線|項目在文件中嵌入|  
|調整大小控點|項目目前已選取|  
|將矩形內外的串聯框線|項目目前是就地啟動|  
|影線樣式重疊項目。|項目的伺服器為開啟狀態|  
  
 您可以輕易地處理這個初始化使用檢查 OLE 項目狀態並設定適當的樣式的程序。  在 OCLIENT 範例中找到的 **SetupTracker** 函式中追蹤程式初始化。  這個函式的參數是這個 Tracker， *pTracker*位址;要與這個追蹤相關的用戶端項目， `pItem`的指標;而的矩形， *pTrueRect 的*指標。  如需這個函式的更完整的範例，請參閱 MFC OLE [OCLIENT](../top/visual-cpp-samples.md)範例。  
  
 **SetupTracker** 程式碼範例顯示單一函式;函式的行位置顛倒有關函式的功能的討論:  
  
 [!code-cpp[NVC_MFCOClient#1](../mfc/codesnippet/CPP/how-to-implement-tracking-in-your-code_1.cpp)]  
  
 這個 Tracker 將最小大小和清除樣式這台追蹤程式初始化。  
  
 [!code-cpp[NVC_MFCOClient#2](../mfc/codesnippet/CPP/how-to-implement-tracking-in-your-code_2.cpp)]  
  
 下列程式碼會檢查項目目前是否已選取，而項目是否與文件在連結或內嵌。  調整位於框線內的控制代碼加入至樣式，表示項目目前已選取。  如果項目與您的資料連接，使用點狀的框線樣式。  實心框線，否則內嵌，使用項目。  
  
 [!code-cpp[NVC_MFCOClient#3](../mfc/codesnippet/CPP/how-to-implement-tracking-in-your-code_3.cpp)]  
  
 如果項目目前已開啟，下列程式碼以規劃模式重疊項目。  
  
 [!code-cpp[NVC_MFCOClient#4](../mfc/codesnippet/CPP/how-to-implement-tracking-in-your-code_4.cpp)]  
  
 您可以呼叫這個函式，在這個追蹤程式必須顯示。  例如，呼叫從您的檢視類別的 `OnDraw` 函式上執行此功能。  這項更新追蹤程式的外觀，每當檢視重新繪製。  如需完整範例，請參閱 MFC OLE [OCLIENT](../top/visual-cpp-samples.md)範例的 **CMainView::OnDraw** 函式。  
  
 在您的應用程式，需要追蹤程式碼，例如調整大小，移至的事件或點擊偵測，就會發生。  這些動作通常表示嘗試擷取或移動項目。  在這些情況下，您必須決定要擷取了:調整大小控點或之間框線區段的調整大小控點。  `OnLButtonDown` 訊息處理常式是測試滑鼠位置的好有關項目。  呼叫 `CRectTracker::HitTest`。  如果測試傳回或呼叫 **CRectTracker::hitOutside**以外，項目調整大小或移動。  因此，您應該呼叫 `Track` 成員函式。  如需完整範例參閱位於 MFC OLE 範例的 **CMainView::OnLButtonDown** 函式 [OCLIENT](../top/visual-cpp-samples.md) 。  
  
 `CRectTracker` 類別會提供數個不同的游標圖案表示移動時，是否會調整大小，或拖曳作業時發生。  處理這個事件，檢查項目在滑鼠下目前是否已選取。  如果是，請呼叫 `CRectTracker::SetCursor`或呼叫預設的處理常式。  下列範例是從 MFC OLE [OCLIENT](../top/visual-cpp-samples.md)範例:  
  
 [!code-cpp[NVC_MFCOClient#5](../mfc/codesnippet/CPP/how-to-implement-tracking-in-your-code_5.cpp)]  
  
## 請參閱  
 [追蹤器：在 OLE 應用程式中實作追蹤器](../mfc/trackers-implementing-trackers-in-your-ole-application.md)