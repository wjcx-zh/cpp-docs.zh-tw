---
title: "在檢視中繪圖 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "裝置內容, 螢幕繪圖"
  - "繪製, 在檢視中"
  - "在檢視類別中繪製訊息"
  - "列印 [MFC], 檢視"
  - "列印檢視"
  - "檢視, 列印"
  - "檢視, 呈現"
  - "檢視, 更新"
ms.assetid: e3761db6-0f19-4482-a4cd-ac38ef7c4d3a
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 在檢視中繪圖
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

幾乎在應用程式的所有繪製在檢視的 `OnDraw` 成員函式，則檢視類別必須覆寫。例外狀況是滑鼠繪圖，討論 [您可以檢視輸入的解譯使用者](../mfc/interpreting-user-input-through-a-view.md)\)。您的 `OnDraw` 覆寫:  
  
1.  藉由呼叫您提供的文件成員函式取得資料。  
  
2.  藉由呼叫一個裝置內容物件的成員函式顯示資料該框架會傳遞至 `OnDraw`。  
  
 當文件的資料以某種方式變更時，必須重繪檢視以反映變更。  通常，，當使用者藉由檢視進行變更文件中，就會發生這種情況。  在這種情況下，檢視呼叫文件中的 [UpdateAllViews](../Topic/CDocument::UpdateAllViews.md) 成員函式告知在同一份文件的所有檢視自行更新。  `UpdateAllViews` 呼叫每個檢視的 [OnUpdate](../Topic/CView::OnUpdate.md) 成員函式。  `OnUpdate` 的預設實作沒有檢視的整個工作區。  您可以覆寫它無法對應至文件中修改的部分工作區變更的區域。  
  
 類別 \( **CDocument** 的 `UpdateAllViews` 成員函式和類別 `CView` 的 `OnUpdate` 成員函式可讓您透過資訊描述修改文件中的哪個部分。  這個「提示」機制讓您限制檢視必須重新繪製的區域。  `OnUpdate` 會使用兩個「提示」引數。  第一，則為 `lHint`，型別 **LPARAM**，讓您可以使用想要的任何資料，，而第二個， `pHint`， `CObject`型別\*，可讓您透過指標從 `CObject`衍生的任何物件。  
  
 當檢視變成無效時，視窗傳送至 `WM_PAINT` 訊息。  檢視的 [OnPaint](../Topic/CWnd::OnPaint.md) 處理常式函式回應訊息透過建立類別 [CPaintDC](../mfc/reference/cpaintdc-class.md) 裝置內容物件並且呼叫您檢視的 `OnDraw` 成員函式。  您通常不需要撰寫一個被覆寫的 `OnPaint` 處理常式函式。  
  
 [裝置內容。](../mfc/device-contexts.md) 是包含裝置繪圖屬性的相關資訊 \(例如顯示或印表機的 Windows 資料結構。  所有繪製呼叫透過裝置內容物件進行。  對於在螢幕上繪製， `OnDraw` 透過 `CPaintDC` 物件。  如需繪製在印表機，它會為目前印表機設定的 [CDC](../mfc/reference/cdc-class.md) 物件。  
  
 您的繪圖程式碼在這個檢視會先擷取指標至文件，然後將裝置內容進行繪製呼叫。  下列簡單的 `OnDraw` 範例說明流程:  
  
 [!code-cpp[NVC_MFCDocView#1](../mfc/codesnippet/CPP/drawing-in-a-view_1.cpp)]  
  
 在此範例中，您會定義 `GetData` 函式，因為您的衍生類別，資料的成員。  
  
 範例在檢視列印任何字串會從文件中取得，置中。  如果 `OnDraw` 呼叫是螢幕繪製，在 `pDC` 中傳遞的 `CDC` 物件是建構函式已經呼叫 `BeginPaint`的 `CPaintDC` 。  要繪製的函式的呼叫是透過裝置內容指標進行。  如需裝置內容和繪製呼叫的詳細資訊，請參閱《 *MFC* 參考》中的 [與視窗物件一起使用](../mfc/working-with-window-objects.md)和 [CDC](../mfc/reference/cdc-class.md) 類別。  
  
 如需詳細的範例寫入 `OnDraw`，請參閱 [MFC 範例](../top/visual-cpp-samples.md)。  
  
## 請參閱  
 [使用檢視](../mfc/using-views.md)