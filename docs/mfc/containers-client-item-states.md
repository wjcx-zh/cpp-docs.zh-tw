---
title: 容器： 用戶端項目狀態 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE containers [MFC], client-item states
- states, OLE container client-item
- lifetime, lifetime states and OLE container client items
- client items and OLE containers
ms.assetid: e7021caa-bd07-4adb-976e-f5f3d025bc53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c02fb9e695fe206912f360dd1ad9907c6714cf1b
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929714"
---
# <a name="containers-client-item-states"></a>容器：用戶端項目狀態
本文說明不同的用戶端項目在其存留期間通過的狀態。  
  
 用戶端項目會經過數個狀態，如建立、 啟動、 修改和儲存。 每次的項目狀態變更時，這個架構會呼叫[COleClientItem::OnChange](../mfc/reference/coleclientitem-class.md#onchange)與**OLE_CHANGED_STATE**通知。 第二個參數是從值`COleClientItem::ItemState`列舉型別。 它可以是下列其中一項：  
  
-   *COleClientItem::emptyState*  
  
-   *COleClientItem::loadedState*  
  
-   *COleClientItem::openState*  
  
-   *COleClientItem::activeState*  
  
-   *COleClientItem::activeUIState*  
  
 在空的狀態中，用戶端項目還不完全的項目。 已配置記憶體，但是它尚未已初始化 OLE 項目的資料。 這是透過呼叫建立的用戶端項目時的狀態**新**但尚未經過典型的兩個步驟建立第二個步驟。  
  
 在第二個步驟中，執行透過呼叫`COleClientItem::CreateFromFile`或另一個`CreateFrom` *xxxx*函式，完全建立項目。 （從檔案或其他來源，例如剪貼簿） 的 OLE 資料聯`COleClientItem`-衍生物件。 現在項目是以載入狀態。  
  
 當項目具有已在伺服器的視窗中開啟而不是在容器文件中的位置中開啟時，它處於已開啟 （或完全開啟）。 在這個狀態下，交叉影線通常繪製透過容器的視窗，以表示此項目為作用中其他位置中的項目表示。  
  
 當就地啟動項目時，它會將傳遞，通常只短暫，透過使用中狀態。 接著，它會進入 UI 作用狀態，其功能表、 工具列和其他使用者介面元件，與這些容器的伺服器已合併。 這些使用者介面元件存在區別 UI 作用狀態從 作用中狀態。 否則，作用中狀態類似於 UI 作用狀態。 如果伺服器支援復原，需要伺服器。 若要保留 OLE 項目的復原狀態資訊，直到達到載入或開啟狀態  
  
## <a name="see-also"></a>另請參閱  
 [容器](../mfc/containers.md)   
 [啟用](../mfc/activation-cpp.md)   
 [容器： 用戶端項目通知](../mfc/containers-client-item-notifications.md)   
 [追蹤器](../mfc/trackers.md)   
 [CRectTracker 類別](../mfc/reference/crecttracker-class.md)
