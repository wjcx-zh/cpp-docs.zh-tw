---
title: 將訊息對應到函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.mapping.msg.function
dev_langs:
- C++
helpviewer_keywords:
- Windows messages [MFC], adding message handlers
- message maps [MFC], mapping messages to functions
ms.assetid: a7727a62-f638-4b20-b7f5-131f47200d6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3388cd8e9a52ef9aacb427d66b027d793b08ca75
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="mapping-messages-to-functions"></a>將訊息對應到函式
[屬性] 視窗可讓您將訊息處理常式 （MFC 使用者介面類別的成員函式） 的繫結至您的應用程式資源所產生的訊息。 他們使用[MFC 訊息對應](../../mfc/messages-and-commands-in-the-framework.md)建立繫結。  
  
 當您使用類別檢視來建立衍生自其中一個架構類別的新類別時，它會自動放置完整且實用類別標頭 (.h) 和實作 (.cpp) 中您指定的檔案。  
  
> [!NOTE]
>  若要加入的新類別，不會處理訊息，請直接在文字編輯器中建立類別。  
  
### <a name="to-define-or-remove-a-message-handler-using-the-properties-window"></a>若要定義或移除使用 [屬性] 視窗的訊息處理常式  
  
1.  在 類別檢視中，按一下 類別。  
  
2.  在 屬性 視窗中，按一下**訊息** 按鈕。  
  
    > [!NOTE]
    >  **訊息**按鈕時，使用您在 類別檢視 或 當您按一下來源視窗內選取的類別名稱。  
  
     如果您的專案具有訊息處理常式，處理常式的名稱就會出現在右邊的資料行旁邊的訊息。  
  
3.  如果訊息沒有處理常式，然後按一下右邊的資料行中顯示建議的名稱做為處理常式的 [屬性] 視窗中的資料格\<新增 >*HandlerName*。 (例如，`WM_TIMER`訊息處理常式建議\<新增 >`OnTimer`)。  
  
4.  按一下以加入函式的虛設常式程式碼的建議的名稱。  
  
5.  若要編輯訊息處理常式，按兩下 [類別檢視] 中的訊息並編輯 [來源] 視窗中的程式碼。  
  
 若要移除的訊息處理常式，請按兩下右欄中的處理常式，並選取\<刪除 >*HandlerName*。 函式的程式碼標記為註解。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 訊息處理常式](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [使用程式碼精靈加入功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [加入類別](../../ide/adding-a-class-visual-cpp.md)   
 [加入成員函式](../../ide/adding-a-member-function-visual-cpp.md)   
 [加入成員變數](../../ide/adding-a-member-variable-visual-cpp.md)   
 [覆寫虛擬函式](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [加入對話方塊控制項的事件處理常式](../../windows/adding-event-handlers-for-dialog-box-controls.md)   
 [巡覽類別結構](../../ide/navigating-the-class-structure-visual-cpp.md)
