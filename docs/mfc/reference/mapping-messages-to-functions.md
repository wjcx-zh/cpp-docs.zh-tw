---
title: "將訊息對應到函式 | Microsoft Docs"
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
  - "vc.codewiz.mapping.msg.function"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "訊息對應 [C++], 將訊息對應到函式"
  - "Windows 訊息 [C++], 加入訊息處理常式"
ms.assetid: a7727a62-f638-4b20-b7f5-131f47200d6a
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 將訊息對應到函式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\[屬性\] 視窗讓您能夠將訊息處理常式 \(MFC 使用者介面類別的成員函式\) 繫結到應用程式資源所產生的訊息。  它們使用 [MFC 訊息對應](../../mfc/messages-and-commands-in-the-framework.md) \(Message Map\) 建立繫結。  
  
 當使用 \[類別檢視\] 來建立衍生自其中一個架構 \(Framework\) 類別的新類別時，會自動在您指定的標頭檔 \(.h\) 及實作檔 \(.cpp\) 中放置完整並功能齊全的類別。  
  
> [!NOTE]
>  若要加入不處理訊息的新類別，請在文字編輯器中直接建立類別。  
  
### 若要使用屬性視窗來定義或移除訊息處理常式  
  
1.  在 \[類別檢視\] 中，按一下類別。  
  
2.  在 \[屬性\] 視窗中，按一下 \[訊息\] 按鈕。  
  
    > [!NOTE]
    >  當您選取 \[類別檢視\] 中的類別名稱或在來源視窗內按一下時，就可以使用 \[訊息\] 按鈕。  
  
     如果您的專案具有訊息處理常式，則會在訊息旁邊的右欄中出現處理常式名稱。  
  
3.  如果訊息沒有處理常式，請按一下 \[屬性\] 視窗右欄中的儲存格，將處理常式建議的名稱顯示為 \<加入\>*HandlerName*。 \(例如，`WM_TIMER` 訊息處理常式建議 \<加入\>`OnTimer`\)。  
  
4.  按一下建議的名稱，加入函式的 Stub 程式碼。  
  
5.  若要編輯訊息處理常式，請按兩下 \[類別檢視\] 中的訊息並編輯來源視窗中的程式碼。  
  
 若要移除訊息處理常式，請按兩下右欄中的處理常式，並選擇 \<刪除\>*HandlerName*。  函式的程式碼將被轉為註解。  
  
## 請參閱  
 [MFC 訊息處理常式](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [使用程式碼精靈加入功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [加入類別](../../ide/adding-a-class-visual-cpp.md)   
 [加入成員函式](../../ide/adding-a-member-function-visual-cpp.md)   
 [加入成員變數](../../ide/adding-a-member-variable-visual-cpp.md)   
 [覆寫 Virtual 函式](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Adding Event Handlers for Dialog Box Controls](../../mfc/adding-event-handlers-for-dialog-box-controls.md)   
 [巡覽類別結構](../../ide/navigating-the-class-structure-visual-cpp.md)