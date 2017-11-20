---
title: "COM 介面進入點 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- entry points, COM interfaces
- state management, OLE/COM interfaces
- MFC COM, COM interface entry points
- OLE, interface entry points
- MFC, managing state data
- COM interfaces, entry points
ms.assetid: 9e7421dc-0731-4748-9e1b-90acbaf26d77
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4d551c3875a2c8aca235437579db2f467f680380
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="com-interface-entry-points"></a>COM 介面進入點
COM 介面的成員函式，使用[METHOD_PROLOGUE](com-interface-entry-points.md#method_prologue)巨集來維護適當的全域狀態，當呼叫匯出介面的方法。  
  
 通常 `CCmdTarget` 衍生物件所實作介面的成員函式，已使用此巨集來提供 `pThis` 指標的自動初始化。 例如:   
  
 [!code-cpp[NVC_MFCConnectionPoints#5](../mfc/codesnippet/cpp/com-interface-entry-points_1.cpp)]  
  
 如需詳細資訊，請參閱[技術提示 38](../mfc/tn038-mfc-ole-iunknown-implementation.md)關於 MFC/OLE **IUnknown**實作。  
  
 `METHOD_PROLOGUE` 巨集定義如下：  
  
 `#define METHOD_PROLOGUE(theClass, localClass) \`  
  
 `theClass* pThis = \`  
  
 `((theClass*)((BYTE*)this - offsetof(theClass, m_x##localClass))); \`  
  
 `AFX_MANAGE_STATE(pThis->m_pModuleState) \`  
  
 與管理全域狀態相關巨集的部分是：  
  
 `AFX_MANAGE_STATE( pThis->m_pModuleState )`  
  
 在此運算式中， *m_pModuleState*假設為包含物件的成員變數。 將物件具現話化時，運算式會由 `CCmdTarget` 基底類別實作，並且由 `COleObjectFactory` 初始化為適當的值。  
  
## <a name="see-also"></a>另請參閱  
 [管理 MFC 模組的狀態資料](../mfc/managing-the-state-data-of-mfc-modules.md)

