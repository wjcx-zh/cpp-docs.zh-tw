---
title: 定義反映訊息的訊息處理常式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.defining.msg.msghandler
dev_langs:
- C++
helpviewer_keywords:
- messages [MFC], reflected
- message handling [MFC], reflected messages
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3ed941816824c77f14a3364b06af0b3da171ee8f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="defining-a-message-handler-for-a-reflected-message"></a>定義反映訊息的訊息處理常式
當您建立新的 MFC 控制項類別之後時，您可以為它定義訊息處理常式。 反映的訊息處理常式可讓您的控制項類別之前父系所收到的訊息處理自己的訊息。 您可以使用 MFC [CWnd::SendMessage](../../mfc/reference/cwnd-class.md#sendmessage)函式可從您的控制項傳送訊息至父視窗。  
  
 您可以比方說，這項功能建立的清單方塊，將會重繪其本身，而不要依賴要不要這樣 （主控描繪） 之父視窗。 如需有關反映訊息的詳細資訊，請參閱[處理反映訊息](../../mfc/handling-reflected-messages.md)。  
  
 若要建立[ActiveX 控制項](../../mfc/activex-controls-on-the-internet.md)使用相同的功能，您必須建立 ActiveX 控制項專案。  
  
> [!NOTE]
>  您無法加入反映的訊息 (OCM_*訊息*) 為 ActiveX 控制項使用 [屬性] 視窗中，如下所述。 您必須手動加入這些訊息。  
  
### <a name="to-define-a-message-handler-for-a-reflected-message-from-the-properties-window"></a>若要定義反映訊息，從 [屬性] 視窗的訊息處理常式  
  
1.  將控制項，例如清單、 rebar 控制項、 工具列或樹狀目錄控制項，加入至 MFC 專案。  
  
2.  在類別檢視中，按一下您的控制項類別名稱。  
  
3.  在[屬性 視窗](/visualstudio/ide/reference/properties-window)，控制項類別名稱會出現在**類別名稱**清單。  
  
4.  按一下**訊息** 按鈕以顯示可用來加入至控制項的 Windows 訊息。  
  
5.  向下捲動直到您看到標題中的 [屬性] 視窗中的訊息清單**反映**。 或者，按一下**類別**按鈕和摺疊檢視來查看**反映**標題。  
  
6.  選取您要定義處理常式的反映的訊息。 反映的訊息會標示以等號 （=）。  
  
7.  按一下以顯示建議的名稱做為處理常式的 [屬性] 視窗右欄中的資料格\<新增 >*HandlerName*。 (例如， **= WM_CTLCOLOR**訊息處理常式建議\<新增 >**CtlColor**)。  
  
8.  按一下 接受建議的名稱。 處理常式加入至您的專案。  
  
     您新增的訊息處理常式名稱會出現 [反映的訊息] 視窗右欄中。  
  
9. 若要編輯或刪除的訊息處理常式，請重複步驟 4 到 7。 按一下包含要編輯或刪除，然後按一下適當的工作處理常式名稱的資料格。  
  
## <a name="see-also"></a>另請參閱  
 [將訊息對應到函式](../../mfc/reference/mapping-messages-to-functions.md)   
 [使用程式碼精靈加入功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [加入類別](../../ide/adding-a-class-visual-cpp.md)   
 [加入成員函式](../../ide/adding-a-member-function-visual-cpp.md)   
 [加入成員變數](../../ide/adding-a-member-variable-visual-cpp.md)   
 [覆寫虛擬函式](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 訊息處理常式](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [巡覽類別結構](../../ide/navigating-the-class-structure-visual-cpp.md)
