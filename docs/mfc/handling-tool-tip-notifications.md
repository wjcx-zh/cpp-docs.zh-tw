---
title: 處理工具提示告知 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- CToolBarCtrl class [MFC], handling notifications
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: ddb93b5f-2e4f-4537-8053-3453c86e2bbb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8df4b584a4e8b0ef940d5934a5968037427c607d
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931810"
---
# <a name="handling-tool-tip-notifications"></a>處理工具提示告知
當您指定**TBSTYLE_TOOLTIPS**樣式工具列建立和管理工具提示控制項。 工具提示是文字的小型的快顯視窗，其中包含描述工具列按鈕行。 隱藏工具提示，才會出現只有當使用者將游標放在工具列按鈕並等待約二分之一秒。 工具提示會顯示資料指標附近。  
  
 顯示工具提示之前， **TTN_NEEDTEXT**通知訊息會傳送給工具列的主控視窗擷取按鈕的描述性文字。 如果工具列的擁有者視窗`CFrameWnd` 視窗中，而不需要任何額外的工作，會顯示提示，因為工具`CFrameWnd`具有預設處理常式，如**TTN_NEEDTEXT**通知。 如果工具列的擁有者視窗不衍生自`CFrameWnd`，例如對話方塊或表單檢視，您必須將項目加入至主控視窗的訊息對應，並提供訊息對應中的通知處理常式。 主控視窗的訊息對應的項目如下所示：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/cpp/handling-tool-tip-notifications_1.cpp)]  
  
## <a name="remarks"></a>備註  
 `memberFxn`  
 需要此按鈕的文字時所要呼叫此成員函式。  
  
 請注意，工具提示的識別碼一律為 0。  
  
 除了**TTN_NEEDTEXT**通知，工具提示控制項可以傳送下列通知至工具列控制項：  
  
|通知|意義|  
|------------------|-------------|  
|**TTN_NEEDTEXTA**|工具提示控制項需要 ASCII 文字 (僅 Windows 95)|  
|**TTN_NEEDTEXTW**|工具提示控制項需要 UNICODE 文字 (Windows NT)|  
|**TBN_HOTITEMCHANGE**|指出已變更的作用 （反白顯示） 項目。|  
|**NM_RCLICK**|表示使用者已經以滑鼠右鍵按一下按鈕。|  
|**TBN_DRAGOUT**|表示使用者已按一下按鈕，並拖曳出按鈕的指標。 它可讓應用程式實作拖曳和卸除從工具列按鈕。 時收到這項通知，應用程式會開始拖曳和卸除作業。|  
|**TBN_DROPDOWN**|表示使用者已按一下按鈕使用**TBSTYLE_DROPDOWN**樣式。|  
|**TBN_GETOBJECT**|表示使用者將指標移按鈕使用**TBSTYLE_DROPPABLE**樣式。|  
  
 範例處理常式函式及啟用工具提示的詳細資訊，請參閱[工具提示](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [控制項](../mfc/controls-mfc.md)

