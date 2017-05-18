---
title: "將訊息對應到函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.mapping.msg.function
dev_langs:
- C++
helpviewer_keywords:
- Windows messages [C++], adding message handlers
- message maps [C++], mapping messages to functions
ms.assetid: a7727a62-f638-4b20-b7f5-131f47200d6a
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4fafe461008e3545243d693e0d9e34acd57163e0
ms.openlocfilehash: 584cc8b1f59f94d88718add5c21046c487b8556f
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="mapping-messages-to-functions"></a>將訊息對應到函式
[屬性] 視窗可讓您繫結的訊息處理常式 （MFC 使用者介面類別的成員函式） 應用程式的資源所產生的訊息。 他們使用[MFC 訊息對應](../../mfc/messages-and-commands-in-the-framework.md)建立繫結。  
  
 當您建立新的類別衍生自 framework 類別之一來使用類別檢視時，它會放置完整與功能類別的標頭 (.h) 和實作 (.cpp) 中您指定的檔案。  
  
> [!NOTE]
>  若要加入的新類別，不會處理訊息，請直接在文字編輯器中建立的類別。  
  
### <a name="to-define-or-remove-a-message-handler-using-the-properties-window"></a>若要定義或移除訊息的處理常式，使用 [屬性] 視窗  
  
1.  在類別檢視中，按一下 [類別]。  
  
2.  在 [屬性] 視窗中，按一下 [**訊息**] 按鈕。  
  
    > [!NOTE]
    >  **訊息**按鈕時，使用您在 類別檢視，或當您按一下 來源 視窗中選取的類別名稱。  
  
     如果您的專案具有訊息處理常式，處理常式的名稱就會出現在右邊的資料行旁邊的訊息。  
  
3.  如果訊息沒有處理常式，然後按一下 [顯示建議的處理常式做為名稱屬性] 視窗右欄中的儲存格\<新增 >*HandlerName*。 (例如，`WM_TIMER`訊息處理常式建議\<新增 >`OnTimer`)。  
  
4.  按一下要加入函式的虛設常式程式碼的建議的名稱。  
  
5.  若要編輯訊息處理常式，按兩下 [類別檢視] 中的訊息，並編輯 [來源] 視窗中的程式碼。  
  
 若要移除的訊息處理常式，請按兩下右欄中的處理常式，然後選取\<刪除 >*HandlerName*。 函式的程式碼標記為註解。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 訊息處理常式](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [使用程式碼精靈加入功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [加入類別](../../ide/adding-a-class-visual-cpp.md)   
 [加入成員函式](../../ide/adding-a-member-function-visual-cpp.md)   
 [加入成員變數](../../ide/adding-a-member-variable-visual-cpp.md)   
 [覆寫虛擬函式](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [加入對話方塊控制項的事件處理常式](../../windows/adding-event-handlers-for-dialog-box-controls.md)   
 [巡覽類別結構](../../ide/navigating-the-class-structure-visual-cpp.md)

