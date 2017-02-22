---
title: "容器：用戶端項目通知 | Microsoft Docs"
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
  - "告知, 容器用戶端項目"
  - "OLE 容器, 用戶端項目通知"
ms.assetid: e1f1c427-01f5-45f2-b496-c5bce3d76340
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 容器：用戶端項目通知
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文將討論 MFC 架構稱為的可覆寫的函式在伺服器應用程式修改在用戶端應用程式的文件的項目。  
  
 [COleClientItem](../mfc/reference/coleclientitem-class.md) 定義呼叫以回應在元件應用程式的需求，也稱為伺服器應用程式的幾個可覆寫的函式。  這些 overridables 通常做為通知。  這些告知容器應用程式各種事件，例如捲動、啟動或位置的變更，所以，並變更使用者進行時，編輯或管理項目。  
  
 這個架構會呼叫 `COleClientItem::OnChange`，需要實作的可覆寫的函式通知變更的容器應用程式。  這個受保護的函式接受兩個引數。  第一個指定伺服器變更項目的原因:  
  
|告知|意義|  
|--------|--------|  
|`OLE_CHANGED`|OLE 項目的外觀變更時。|  
|`OLE_SAVED`|OLE 項目儲存。|  
|`OLE_CLOSED`|OLE 項目關閉。|  
|**OLE\_RENAMED**|包含 OLE 項目的伺服器檔案重新命名。|  
|`OLE_CHANGED_STATE`|OLE 項目從某個狀態變更為另一個。|  
|**OLE\_CHANGED\_ASPECT**|架構變更 OLE 項目的繪製方式。|  
  
 這些值是從 **OLE\_NOTIFICATION** 列舉，在 AFXOLE.H. 定義。  
  
 對這個函式的第二個引數會指定項目有何變更或什麼狀態並輸入:  
  
|當第一個引數是|第二個引數。|  
|-------------|------------|  
|`OLE_SAVED` 或 `OLE_CLOSED`|不使用。|  
|`OLE_CHANGED`|指定變更 OLE 項目的外觀。|  
|`OLE_CHANGED_STATE`|描述輸入的狀態 \( **loadedState**、`emptyState`、 `openState`、 `activeState`或 `activeUIState`\)。|  
  
 如需用戶端項目可以假設狀態的詳細資訊，請參閱 [容器:用戶端項目狀態](../mfc/containers-client-item-states.md)。  
  
 當項目為就地編譯時，就會啟動這個框架呼叫 `COleClientItem::OnGetItemPosition` 。  實作針對支援就地編譯的應用程式所需的。  MFC 應用程式精靈提供基底實作，指定項目的座標的 `CRect` 物件當做引數傳遞至 `OnGetItemPosition`。  
  
 在就地編輯期間，如果 OLE 項目的位置或大小變更時，該項目的位置的容器的相關資訊和裁剪方框必須更新，以及伺服器必須取得有關變更的資訊。  這個架構提供此呼叫 `COleClientItem::OnChangeItemPosition` 。  MFC 應用程式精靈提供呼叫基底類別的函式的覆寫。  您必須編輯函式應用程式精靈為您的 `COleClientItem`衍生類別覆寫，以便函式更新您的用戶端項目物件保留的所有資訊。  
  
## 請參閱  
 [容器](../mfc/containers.md)   
 [容器：用戶端項目狀態](../mfc/containers-client-item-states.md)   
 [COleClientItem::OnChangeItemPosition](../Topic/COleClientItem::OnChangeItemPosition.md)