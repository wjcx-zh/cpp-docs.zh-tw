---
title: "COM 介面進入點 | Microsoft Docs"
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
  - "COM 介面, 進入點"
  - "進入點, COM 介面"
  - "MFC COM, COM 介面進入點"
  - "MFC, 管理狀態資料"
  - "OLE, 介面進入點"
  - "狀態管理, OLE/COM 介面"
ms.assetid: 9e7421dc-0731-4748-9e1b-90acbaf26d77
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COM 介面進入點
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

對於 COM 介面的成員函式，請使用 [METHOD\_PROLOGUE](../Topic/METHOD_PROLOGUE.md) 巨集維護適當的全域狀態，當呼叫匯出方法的介面。  
  
 通常， `CCmdTarget`實作的介面成員函式衍生物件已經使用這個巨集會提供 `pThis` 指標的自動初始化。  例如：  
  
 [!code-cpp[NVC_MFCConnectionPoints#5](../mfc/codesnippet/CPP/com-interface-entry-points_1.cpp)]  
  
 如需詳細資訊，請參閱MFC\/OLE **IUnknown** 實作的 [Technical Note 38](../mfc/tn038-mfc-ole-iunknown-implementation.md) 。  
  
 `METHOD_PROLOGUE` 巨集定義如下：  
  
 `#define METHOD_PROLOGUE(theClass, localClass) \`  
  
 `theClass* pThis = \`  
  
 `((theClass*)((BYTE*)this - offsetof(theClass, m_x##localClass))); \`  
  
 `AFX_MANAGE_STATE(pThis->m_pModuleState) \`  
  
 與處理全域狀態相關的巨集的部分是:  
  
 `AFX_MANAGE_STATE( pThis->m_pModuleState )`  
  
 在這個運算式， *m\_pModuleState* 假設是包含物件的成員變數。  將物件具現化時，它會由 `CCmdTarget` 基底類別實作和初始化為適當的值是 `COleObjectFactory`。  
  
## 請參閱  
 [管理 MFC 模組的狀態資料](../mfc/managing-the-state-data-of-mfc-modules.md)