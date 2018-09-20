---
title: 容器： 用戶端項目通知 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], container client item
- OLE containers [MFC], client-item notifications
- client items and OLE containers
ms.assetid: e1f1c427-01f5-45f2-b496-c5bce3d76340
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5db5170b6c946e4bfeda99a3275f045a07fc9beb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435216"
---
# <a name="containers-client-item-notifications"></a>容器：用戶端項目通知

這篇文章討論 MFC 架構會呼叫伺服器應用程式修改用戶端應用程式的文件中的項目時的可覆寫函式。

[COleClientItem](../mfc/reference/coleclientitem-class.md)定義數個可覆寫的函式所呼叫之元件的應用程式，也稱為伺服器應用程式要求回應中。 這些可覆寫通常做為通知。 這些通知容器應用程式的各種事件，例如捲動，啟動過程中或變更位置，以及編輯或其他操作的項目時，可讓使用者的變更。

架構會通知您的容器應用程式的變更，透過呼叫`COleClientItem::OnChange`，其實作是必要的可覆寫函式。 此受保護的函式會接收兩個引數。 第一個指定伺服器變更之項目的的原因：

|通知|意義|
|------------------|-------------|
|**OLE_CHANGED**|OLE 項目的外觀已變更。|
|**OLE_SAVED**|已儲存 OLE 項目。|
|**OLE_CLOSED**|已關閉 OLE 項目。|
|**OLE_RENAMED**|已重新命名伺服器文件，包含 OLE 項目。|
|**OLE_CHANGED_STATE**|OLE 項目已變更是從某個狀態到另一個。|
|**OLE_CHANGED_ASPECT**|OLE 項目的繪圖外觀已變更的架構。|

這些值是從**OLE_NOTIFICATION** AFXOLE 中定義的列舉。H.

此函式的第二個引數會指定如何變更的項目或項目狀態已進入：

|第一個引數時|第二個引數|
|----------------------------|---------------------|
|**OLE_SAVED**或**OLE_CLOSED**|不會使用。|
|**OLE_CHANGED**|指定 OLE 項目已變更的外觀。|
|**OLE_CHANGED_STATE**|描述輸入的狀態 (*emptyState*， *loadedState*， *openState*， *activeState*，或*activeUIState*)。|

如需用戶端項目可以假設之狀態的詳細資訊，請參閱[容器： 用戶端項目狀態](../mfc/containers-client-item-states.md)。

這個架構會呼叫`COleClientItem::OnGetItemPosition`時就地編輯為啟動項目。 支援就地編輯的應用程式需要實作。 MFC 應用程式精靈提供了基本的實作，這會指派至項目的座標`CRect`做為引數傳遞的物件`OnGetItemPosition`。

如果 OLE 項目的位置或大小變更就地編輯時，必須更新項目的位置和裁剪矩形的容器的資訊，而且 server 必須收到變更的相關資訊。 這個架構會呼叫`COleClientItem::OnChangeItemPosition`針對此目的。 MFC 應用程式精靈提供覆寫呼叫基底類別的函式。 您應該編輯應用程式精靈會為撰寫的函式程式`COleClientItem`-衍生類別，以便函式會更新您的用戶端項目物件所保留的任何資訊。

## <a name="see-also"></a>另請參閱

[容器](../mfc/containers.md)<br/>
[容器：用戶端項目狀態](../mfc/containers-client-item-states.md)<br/>
[COleClientItem::OnChangeItemPosition](../mfc/reference/coleclientitem-class.md#onchangeitemposition)

