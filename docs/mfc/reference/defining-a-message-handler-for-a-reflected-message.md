---
title: "定義反映訊息的訊息處理常式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.defining.msg.msghandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "訊息處理, 反映訊息"
  - "訊息, 反映"
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 定義反映訊息的訊息處理常式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建立新的 MFC 控制項類別之後，您就可定義它的訊息處理常式。  反映訊息處理常式讓您的控制項類別能夠優先處理自己的訊息，然後父代 \(Parent\) 才能接收訊息。  您可使用 MFC [CWnd::SendMessage](../Topic/CWnd::SendMessage.md) 函式將訊息從您的控制項傳送到父視窗。  
  
 例如，您可使用此功能來建立能自行重繪 \(Redraw\) 的清單方塊，而不需要依賴父視窗 \(主控描繪 \(Owner\-Draw\)\)。  如需反映訊息的詳細資訊，請參閱[處理反映訊息](../../mfc/handling-reflected-messages.md)。  
  
 若要建立具有同一功能的 [ActiveX 控制項](../../mfc/activex-controls-on-the-internet.md)，您必須建立 ActiveX 控制項的專案。  
  
> [!NOTE]
>  您無法如下文所述，使用 \[屬性\] 視窗來加入 ActiveX 控制項的反映訊息 \(OCM\_*Message*\)。  您必須手動加入訊息。  
  
### 若要從屬性視窗定義反映訊息的訊息處理常式  
  
1.  將諸如清單、Rebar 控制項、工具列或樹狀目錄控制項之類的控制項加入至您的 MFC 專案中。  
  
2.  在 \[類別檢視\] 中，按一下控制項類別的名稱。  
  
3.  在[屬性視窗](../Topic/Properties%20Window.md)中，\[**類別名稱**\] 清單中會出現控制項類別名稱。  
  
4.  按一下 \[訊息\] 按鈕，以顯示可加入至控制項的 Windows 訊息。  
  
5.  向下捲動 \[屬性\] 視窗中的訊息清單，直到看到標題 \[反映\]。  或者，按一下 \[**種類**\] 按鈕並摺疊檢視，以找出 \[反映\] 標題。  
  
6.  選擇您要定義處理常式的反映訊息。  反映訊息係以等號 \(\=\) 標記。  
  
7.  請按 \[屬性\] 視窗右欄中的儲存格，以顯示如 \<add\>*HandlerName* 的處理常式建議名稱 \(例如，**\=WM\_CTLCOLOR** 訊息處理常式建議 \<add\>**CtlColor**\)。  
  
8.  按一下要接受的建議名稱。  處理常式已加入至您的專案中。  
  
     反映訊息視窗的右欄會出現已加入的訊息處理常式名稱。  
  
9. 若要編輯或刪除訊息處理常式，請重複步驟 4 到 7。  按一下包含所要編輯或刪除的訊息處理常式名稱的儲存格，並且按一下適合的工作。  
  
## 請參閱  
 [將訊息對應到函式](../../mfc/reference/mapping-messages-to-functions.md)   
 [使用程式碼精靈加入功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [加入類別](../../ide/adding-a-class-visual-cpp.md)   
 [加入成員函式](../../ide/adding-a-member-function-visual-cpp.md)   
 [加入成員變數](../../ide/adding-a-member-variable-visual-cpp.md)   
 [覆寫 Virtual 函式](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 訊息處理常式](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [巡覽類別結構](../../ide/navigating-the-class-structure-visual-cpp.md)