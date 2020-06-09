---
title: 容器：用戶端項目狀態
ms.date: 11/04/2016
helpviewer_keywords:
- OLE containers [MFC], client-item states
- states, OLE container client-item
- lifetime, lifetime states and OLE container client items
- client items and OLE containers
ms.assetid: e7021caa-bd07-4adb-976e-f5f3d025bc53
ms.openlocfilehash: 927211ccec35d8ec26e2f76b971c59b80248ab96
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625994"
---
# <a name="containers-client-item-states"></a>容器：用戶端項目狀態

本文說明用戶端專案在其存留期內經歷的不同狀態。

用戶端專案會在建立、啟動、修改和儲存時，經歷數個狀態。 每次專案的狀態變更時，架構都會以**OLE_CHANGED_STATE**通知來呼叫[COleClientItem：： OnChange](reference/coleclientitem-class.md#onchange) 。 第二個參數是列舉中的值 `COleClientItem::ItemState` 。 可以是下列其中一項：

- *COleClientItem：： emptyState*

- *COleClientItem：： loadedState*

- *COleClientItem：： openState*

- *COleClientItem：： activeState*

- *COleClientItem：： activeUIState*

在空白狀態中，用戶端專案尚未完全是專案。 記憶體已配置給它，但尚未使用 OLE 專案的資料進行初始化。 這是當用戶端專案是透過呼叫**new**所建立，但尚未經過一般雙步驟建立的第二個步驟時，所使用的狀態。

在第二個步驟中，透過呼叫 `COleClientItem::CreateFromFile` 或另一個 `CreateFrom` *xxxx*函數來執行，此專案已完全建立。 OLE 資料（來自檔案或其他來源，例如剪貼簿）已與 `COleClientItem` 衍生物件相關聯。 現在專案處於已載入狀態。

當專案已在伺服器的視窗中開啟，而不是在容器的檔中開啟時，它會處於開啟（或完全開啟）狀態。 在此狀態下，通常會在容器視窗中的專案表示上繪製交叉影線，表示該專案在別處作用。

當專案已就地啟用時，它通常只會透過使用中狀態傳遞。 然後，它會進入 UI 作用中狀態，其中伺服器已將其功能表、工具列和其他使用者介面元件與容器的控制項合併。 這些使用者介面元件的存在，會區分作用中狀態的 UI 作用中狀態。 否則，作用中狀態會類似于 UI 作用中狀態。 如果伺服器支援復原，則伺服器必須保留 OLE 專案的復原狀態資訊，直到它達到載入或開啟狀態為止。

## <a name="see-also"></a>另請參閱

[容器](containers.md)<br/>
[啟用](activation-cpp.md)<br/>
[容器：用戶端項目通知](containers-client-item-notifications.md)<br/>
[追蹤器](trackers.md)<br/>
[CRectTracker 類別](reference/crecttracker-class.md)
