---
title: 訊息與使用者介面物件相關聯的類型 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.uiobject.msgs
dev_langs:
- C++
helpviewer_keywords:
- message types and user interface objects [MFC]
ms.assetid: 681ee1a7-f6e6-4ea0-9fc6-1fb53a35516e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 14a2309556ca6c5204247ccbe916aebe472a1da1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373420"
---
# <a name="message-types-associated-with-user-interface-objects"></a>與使用者介面物件關聯的訊息類型
下表顯示與您工作時，物件的型別和訊息與其相關聯的型別。  
  
### <a name="user-interface-objects-and-associated-messages"></a>使用者介面物件和相關聯的訊息  
  
|物件識別碼|訊息|  
|---------------|--------------|  
|代表包含視窗的類別名稱|適當的 Windows 訊息[CWnd](../../mfc/reference/cwnd-class.md)-衍生的類別： 對話方塊、 視窗、 子視窗、 MDI 子視窗或最上層框架視窗。|  
|功能表或快速鍵的識別項|-   **命令**訊息 （執行程式的函式）。<br />-   **UPDATE_COMMAND_UI**訊息 （以動態方式更新功能表項目）。|  
|控制識別項|選取的控制項類型的控制項通知訊息。|  
  
## <a name="see-also"></a>另請參閱  
 [將訊息對應到函式](../../mfc/reference/mapping-messages-to-functions.md)   
 [使用程式碼精靈加入功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [加入類別](../../ide/adding-a-class-visual-cpp.md)   
 [加入成員函式](../../ide/adding-a-member-function-visual-cpp.md)   
 [加入成員變數](../../ide/adding-a-member-variable-visual-cpp.md)   
 [覆寫虛擬函式](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 訊息處理常式](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [巡覽類別結構](../../ide/navigating-the-class-structure-visual-cpp.md)
