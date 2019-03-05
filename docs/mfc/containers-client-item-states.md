---
title: 容器：用戶端項目狀態
ms.date: 11/04/2016
helpviewer_keywords:
- OLE containers [MFC], client-item states
- states, OLE container client-item
- lifetime, lifetime states and OLE container client items
- client items and OLE containers
ms.assetid: e7021caa-bd07-4adb-976e-f5f3d025bc53
ms.openlocfilehash: 1453ba3f96e49cefc9014a93ebcfbcfe5c6bc905
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273669"
---
# <a name="containers-client-item-states"></a>容器：用戶端項目狀態

這篇文章會說明不同的用戶端項目在其存留期間通過的狀態。

用戶端項目會經過數個狀態，因為它是建立、 啟動、 修改和儲存。 每次的項目狀態變更，這個架構會呼叫[COleClientItem::OnChange](../mfc/reference/coleclientitem-class.md#onchange)具有**OLE_CHANGED_STATE**通知。 第二個參數是從值`COleClientItem::ItemState`列舉型別。 它可以是下列其中一項：

- *COleClientItem::emptyState*

- *COleClientItem::loadedState*

- *COleClientItem::openState*

- *COleClientItem::activeState*

- *COleClientItem::activeUIState*

在空的狀態中，用戶端項目還不完全的項目。 已配置記憶體，但是它具有尚未初始化 OLE 項目的資料。 這是透過呼叫建立的用戶端項目時的狀態**新**但尚未經過一般的兩個步驟建立的第二個步驟。

在第二個步驟中，執行透過呼叫`COleClientItem::CreateFromFile`或另一部`CreateFrom` *xxxx*函式，完全建立項目。 OLE 資料 （從檔案或其他來源，例如剪貼簿） 聯`COleClientItem`-衍生物件。 現在的項目是載入的狀態。

當項目具有已在伺服器的視窗中開啟而不是在容器文件中的位置中開啟時，它會處於開啟 （或完全開啟） 的狀態。 在此狀態時，交叉影線通常繪製透過容器的視窗，以表示項目為作用中其他位置中的項目表示。

當已就地啟動項目時，會傳遞，通常僅簡單地說，透過作用中狀態。 然後，它會進入 UI 作用狀態，其功能表、 工具列和容器與其他使用者介面元件，已合併伺服器。 這些使用者介面元件存在區別 UI 作用狀態，從作用中狀態。 否則，作用中狀態類似於 UI 作用狀態。 如果伺服器支援復原，需要伺服器。 若要保留 OLE 項目的復原狀態資訊，直到它到達載入或開啟狀態

## <a name="see-also"></a>另請參閱

[容器](../mfc/containers.md)<br/>
[啟動](../mfc/activation-cpp.md)<br/>
[容器：用戶端項目通知](../mfc/containers-client-item-notifications.md)<br/>
[追蹤器](../mfc/trackers.md)<br/>
[CRectTracker 類別](../mfc/reference/crecttracker-class.md)
