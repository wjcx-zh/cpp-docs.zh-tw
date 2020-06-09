---
title: 容器：用戶端項目通知
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], container client item
- OLE containers [MFC], client-item notifications
- client items and OLE containers
ms.assetid: e1f1c427-01f5-45f2-b496-c5bce3d76340
ms.openlocfilehash: 54b1b2a64685b00fb265e0f80c1f6ad878a7da85
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623023"
---
# <a name="containers-client-item-notifications"></a>容器：用戶端項目通知

本文討論當伺服器應用程式修改用戶端應用程式檔中的專案時，MFC 架構所呼叫的可覆寫函式。

[COleClientItem](reference/coleclientitem-class.md)會定義數個可覆寫的函式，以回應來自元件應用程式（也稱為伺服器應用程式）的要求。 這些 overridables 通常會作為通知。 它們會通知容器應用程式各種事件，例如滾動、啟動或位置變更，以及使用者在編輯或操作專案時所進行的變更。

架構會透過呼叫來通知您的容器應用程式變更 `COleClientItem::OnChange` ，此函式需要其實作為必要的可覆寫函數。 這個受保護的函式會接收兩個引數。 第一個會指定伺服器變更專案的原因：

|通知|意義|
|------------------|-------------|
|**OLE_CHANGED**|OLE 專案的外觀已經變更。|
|**OLE_SAVED**|已儲存 OLE 專案。|
|**OLE_CLOSED**|OLE 專案已關閉。|
|**OLE_RENAMED**|包含 OLE 專案的伺服器檔已經重新命名。|
|**OLE_CHANGED_STATE**|OLE 專案已從某個狀態變更為另一個。|
|**OLE_CHANGED_ASPECT**|架構已變更 OLE 專案的繪製層面。|

這些值來自于 AFXOLE 中定義的**OLE_NOTIFICATION**列舉。H.

此函式的第二個引數會指定專案變更的方式，或其所輸入的狀態：

|當第一個引數為|二個引數|
|----------------------------|---------------------|
|**OLE_SAVED**或**OLE_CLOSED**|未使用。|
|**OLE_CHANGED**|指定已變更之 OLE 專案的層面。|
|**OLE_CHANGED_STATE**|描述所輸入的狀態（*emptyState*、 *loadedState*、 *openState*、 *activeState*或*activeUIState*）。|

如需用戶端專案可假設之狀態的詳細資訊，請參閱[容器：用戶端專案狀態](containers-client-item-states.md)。

架構會在 `COleClientItem::OnGetItemPosition` 專案啟用時進行就地編輯時呼叫。 支援就地編輯的應用程式需要執行。 MFC 應用程式精靈提供基本的實作為，它會將專案的座標指派給當做 `CRect` 引數傳遞至的物件 `OnGetItemPosition` 。

如果 OLE 專案的位置或大小在就地編輯期間變更，則必須更新該專案的位置和裁剪矩形的相關資訊，且伺服器必須接收變更的相關資訊。 此架構會 `COleClientItem::OnChangeItemPosition` 針對此目的進行呼叫。 MFC 應用程式精靈會提供呼叫基類功能的覆寫。 您應該編輯應用程式精靈針對衍生類別所撰寫的函 `COleClientItem` 式，讓函式更新您的用戶端專案物件所保留的任何資訊。

## <a name="see-also"></a>另請參閱

[容器](containers.md)<br/>
[容器：用戶端項目狀態](containers-client-item-states.md)<br/>
[COleClientItem：： OnChangeItemPosition](reference/coleclientitem-class.md#onchangeitemposition)
