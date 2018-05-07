---
title: 容器： 用戶端項目通知 |Microsoft 文件
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
ms.openlocfilehash: 2255f28c1250096bfbeb1a9365c57f78e17e20d7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="containers-client-item-notifications"></a>容器：用戶端項目通知
本文討論 MFC 架構在伺服器應用程式修改用戶端應用程式的文件中的項目時所呼叫的可覆寫函式。  
  
 [COleClientItem](../mfc/reference/coleclientitem-class.md)定義數個呼叫的可覆寫函式以回應從元件的應用程式，這也稱為伺服器應用程式的要求。 這些可覆寫通常做為通知。 這些通知容器應用程式的各種事件，例如捲動、 啟動或變更位置，以及編輯或其他操作項目時，可讓使用者的變更。  
  
 架構會告知容器應用程式透過呼叫變更的`COleClientItem::OnChange`，其實作是必要的可覆寫函式。 此受保護的函式會接收兩個引數。 第一個指定的伺服器已變更之項目的的原因：  
  
|通知|意義|  
|------------------|-------------|  
|`OLE_CHANGED`|OLE 項目的外觀已變更。|  
|`OLE_SAVED`|已儲存 OLE 項目。|  
|`OLE_CLOSED`|OLE 項目已關閉。|  
|**OLE_RENAMED**|伺服器文件，包含 OLE 項目已重新命名。|  
|`OLE_CHANGED_STATE`|OLE 項目已從某個狀態變更為另一個。|  
|**OLE_CHANGED_ASPECT**|OLE 項目的繪圖外觀架構已變更。|  
  
 這些值是從**OLE_NOTIFICATION** AFXOLE 中定義的列舉。H.  
  
 此函式的第二個引數會指定如何變更的項目或它已經進入狀態：  
  
|當第一個引數是|第二個引數|  
|----------------------------|---------------------|  
|`OLE_SAVED` 或 `OLE_CLOSED`|不使用。|  
|`OLE_CHANGED`|指定 OLE 項目已變更的外觀。|  
|`OLE_CHANGED_STATE`|描述輸入的狀態 (`emptyState`， **loadedState**， `openState`， `activeState`，或`activeUIState`)。|  
  
 如需可以假設用戶端項目狀態的詳細資訊，請參閱[容器： 用戶端項目狀態](../mfc/containers-client-item-states.md)。  
  
 這個架構會呼叫`COleClientItem::OnGetItemPosition`為就地編輯時啟動項目。 支援就地編輯應用程式需要實作。 MFC 應用程式精靈提供的基本實作，會指派至項目的座標`CRect`傳遞做為引數物件`OnGetItemPosition`。  
  
 如果 OLE 項目的位置或大小變更就地編輯時，必須更新容器的資訊項目的位置和裁剪方框，而且伺服器必須接收變更的相關資訊。 這個架構會呼叫`COleClientItem::OnChangeItemPosition`針對此目的。 MFC 應用程式精靈提供覆寫呼叫基底類別的函式。 您應該編輯應用程式精靈為撰寫的函式您`COleClientItem`-衍生類別，使函式會更新用戶端項目的物件所保留的任何資訊。  
  
## <a name="see-also"></a>另請參閱  
 [容器](../mfc/containers.md)   
 [容器： 用戶端項目狀態](../mfc/containers-client-item-states.md)   
 [COleClientItem::OnChangeItemPosition](../mfc/reference/coleclientitem-class.md#onchangeitemposition)

