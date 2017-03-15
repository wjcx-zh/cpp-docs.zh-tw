---
title: "容器：用戶端項目狀態 | Microsoft Docs"
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
  - "用戶端項目與 OLE 容器"
  - "存留期, 存留期狀態和 OLE 容器用戶端項目"
  - "OLE 容器, 用戶端項目狀態"
  - "狀態, OLE 容器用戶端項目"
ms.assetid: e7021caa-bd07-4adb-976e-f5f3d025bc53
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 容器：用戶端項目狀態
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文將存留期將說明不同的狀態用戶端項目傳遞。  
  
 在建立，啟動，已修改，並儲存，用戶端項目經過幾個狀態。  每次項目的檢視狀態變更，架構會與 `OLE_CHANGED_STATE` 通知的 [COleClientItem::OnChange](../Topic/COleClientItem::OnChange.md) 。  第二個參數是從 **COleClientItem::ItemState** 列舉型別的值。  它可以是下列其中一項:  
  
-   **COleClientItem::emptyState**  
  
-   **COleClientItem::loadedState**  
  
-   **COleClientItem::openState**  
  
-   **COleClientItem::activeState**  
  
-   **COleClientItem::activeUIState**  
  
 在 null 狀態，用戶端項目並不完全是項目。  記憶體已配置的，不過，它未初始化 OLE 項目的資料。  這是用戶端項目的狀態時所傳遞至，但未接受一般兩個步驟建立的第二個步驟的 **new** 的呼叫所建立。  
  
 在第二個步驟，執行透過呼叫 `COleClientItem::CreateFromFile` 或其他 **CreateFrom***xxxx* 函式，項目完全建立。  OLE 資料 \(從檔案或其他來源，例如剪貼簿\) 相關聯的 `COleClientItem`衍生物件。  現在項目處於已載入狀態。  
  
 當項目在伺服器上的 Windows 到位在容器文件時開啟而不是開啟，它在開啟 \(或完全開啟\) 狀態。  在這個狀態，交叉陰影線通常會繪製在項目的表示在容器的視窗來表示該項目已在別處為作用中。  
  
 當項目就地啟動時，它，通常只會短暫，透過現用狀態。  然後輸入 UI 作用中狀態，伺服器與容器合併其功能表、工具列和其他使用者介面元件。  這些使用者介面元件會與現用狀態差異 UI 作用中狀態。  否則，現用狀態類似 UI 作用中狀態。  如果為，伺服器需要伺服器支援繼續保留 OLE 項目的復原狀態資訊，直到達到載入或開啟狀態。  
  
## 請參閱  
 [容器](../mfc/containers.md)   
 [啟用](../mfc/activation-cpp.md)   
 [容器：用戶端項目通知](../mfc/containers-client-item-notifications.md)   
 [追蹤器](../mfc/trackers.md)   
 [CRectTracker Class](../mfc/reference/crecttracker-class.md)