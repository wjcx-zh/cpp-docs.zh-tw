---
title: 樹狀目錄控制項通知訊息 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], tree controls
- messages [MFC], notification
- CTreeCtrl class [MFC], notifications
- notifications [MFC], CTreeCtrl
- tree controls [MFC], notification messages
ms.assetid: ac7013b4-91dd-4668-bd75-439ca0680ef9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f7c352da9f9283f53c926a8223984620ee7fa6ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385732"
---
# <a name="tree-control-notification-messages"></a>樹狀目錄控制項通知訊息
樹狀目錄控制項 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 會傳送下列通知訊息做為**WM_NOTIFY**訊息：  
  
|通知訊息|描述|  
|--------------------------|-----------------|  
|**TVN_BEGINDRAG**|表示在拖放作業的開始|  
|**TVN_BEGINLABELEDIT**|表示開始的位置在標籤編輯|  
|**TVN_BEGINRDRAG**|表示開始拖放作業時，使用滑鼠右鍵|  
|**TVN_DELETEITEM**|表示特定項目的刪除|  
|**TVN_ENDLABELEDIT**|表示標籤編輯的結束|  
|**TVN_GETDISPINFO**|若要顯示的項目所需要樹狀結構控制項中的要求資訊|  
|**TVN_ITEMEXPANDED**|訊號子項目的父項目清單的展開或摺疊|  
|**TVN_ITEMEXPANDING**|信號子項目的父項目清單將要展開或摺疊|  
|**TVN_KEYDOWN**|表示鍵盤事件|  
|**TVN_SELCHANGED**|選取項目已從一個項目變更為另一個的訊號|  
|**TVN_SELCHANGING**|表示即將變更為另一項目選取|  
|**TVN_SETDISPINFO**|若要更新的項目所維護的資訊通知|  
  
## <a name="see-also"></a>另請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)

