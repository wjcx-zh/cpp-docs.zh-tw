---
title: "編輯後繼續的錯誤和警告 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ENC2001"
  - "ENC1006"
  - "ENC2008"
  - "ENC1009"
  - "ENC1002"
  - "ENC2002"
  - "ENC1011"
  - "ENC1003"
  - "ENC1004"
  - "ENC1008"
  - "ENC1013"
  - "ENC2005"
  - "ENC1010"
  - "ENC2004"
  - "ENC1007"
  - "ENC1005"
  - "ENC2006"
  - "ENC1001"
  - "ENC2007"
  - "ENC2003"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "編輯後繼續 [C++], 錯誤和警告"
  - "錯誤 [C++], 編輯後繼續"
  - "錯誤 [偵錯工具], 編輯後繼續"
ms.assetid: b5c5e25c-7ca4-4ca9-b91e-e8882de44dae
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "susanno"
manager: "douge"
---
# 編輯後繼續的錯誤和警告 (C++)
[!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)] \[編輯後繼續\] 可讓您在中斷模式停止程式執行、變更執行中的程式碼，然後以新加入的變更繼續執行程式。  
  
 通常會禁止影響類別之公用結構的宣告式程式碼編輯，而且不允許對類別內的方法、屬性主體或私用宣告進行某些編輯。  \[編輯後繼續\] 會盡可能將無法編輯的程式碼標示為淺灰色，並顯示錯誤訊息。  如需 [!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)] 的 \[編輯後繼續\] 中不支援之編輯的詳細資訊，請參閱 [編輯後繼續 \(Visual C\+\+\)](../Topic/Edit%20and%20Continue%20\(Visual%20C++\).md)。  
  
 \[編輯後繼續\] 的錯誤和警告可以透過下列其中一種方式解決：  
  
|解決方式|錯誤和警告訊息編號|  
|----------|---------------|  
|停止偵錯、重新套用變更，然後繼續進行偵錯。|1001、1002、1003、1004、1005、1006、1007、1008、1010、1013、2003、2005。如需此分類的錯誤和警告訊息清單，請參閱[重新啟動偵錯的訊息](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_RestartDebuggingMessages)。|  
|在 \[**編輯**\] 功能表上選擇 \[**復原**\]，然後繼續對未變更的程式碼進行偵錯。<br /><br /> \-或\-<br /><br /> 停止偵錯、重新套用變更，然後繼續進行偵錯。|1009、1011。如需此分類的錯誤和警告訊息清單，請參閱[復原或停止的訊息](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_UndoOrStopMessages)。|  
|繼續偵錯。  在第一次遇到程式碼時會忽略您的變更，但是會在後續呼叫中套用。|2001, 2002, 2004.  如需此分類的錯誤和警告訊息清單，請參閱[下一次呼叫時套用的訊息](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_ApplyAtNextCallMessages)。|  
|執行某些其他動作，例如，重設中斷點或使用目前的 [!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)]版本重建模組。|2007, 2008.  如需此分類的錯誤和警告訊息清單，請參閱[需要執行其他動作的訊息](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_OtherActionRequiredMessages)。|  
  
##  <a name="BKMK_RestartDebuggingMessages"></a> 重新啟動偵錯的訊息  
 下列錯誤訊息必須透過停止目前的偵錯工作階段、重新套用您進行的編輯，然後重新啟動偵錯工作階段的方式解決。  
  
|||  
|-|-|  
|1001|無法更新下列符號的 Thunk，必須先終止偵錯: *symbol* \(位置: *location*，thunk: *address*\)|  
|1002|資料符號已經變更: symbol \(*symbol*\)|  
|1003|無法對應新函式的 Thunk: *function*|  
|1004|無法開啟類型封裝的 PDB: *pdb* \(pdb\)|  
|1005|已經重新命名、移除或修改符號: *symbol*|  
|1006|加入、重新命名、移除了全域或靜態變數，或變更了全域或靜態變數的資料型別或初始化: *symbol* \(*module* 所參考\)|  
|1007|未定義符號: *symbol* \(*module* 所參考\)|  
|1008|無法在編輯時為載入的物件執行所需的執行階段初始化: *module*|  
|1010|加入了靜態或全域變數: *variable referenced in file*|  
|1013|套用程式碼變更時，偵錯工具記憶體不足|  
|2003|程式碼位置變更可能造成例外狀況處理或變數解構錯誤: *function*|  
|2005|新的來源提供給程式碼。  可能影響偵錯工具的行號資訊: function \(*function*\)|  
  
##  <a name="BKMK_UndoOrStopMessages"></a> 復原或停止的訊息  
 下列錯誤訊息可以透過停止目前的偵錯工作階段、重新套用您進行的編輯，然後重新啟動偵錯工作階段的方式解決。  
  
-   在 \[編輯\] 功能表上，按一下 \[復原\]。  您可以繼續偵錯，不過不會套用您的編輯內容。  
  
     \-或\-  
  
-   停止偵錯、重新套用編輯，然後重新啟動偵錯。  
  
|||  
|-|-|  
|1009|刪除了靜態或全域變數: *variable referenced in file*|  
|1011|變更了靜態或全域變數: *variable referenced in file*|  
  
##  <a name="BKMK_ApplyAtNextCallMessages"></a> 下一次呼叫時套用的訊息  
 下列其中一個警告訊息顯示時，您可以繼續您的偵錯工作階段。  在編輯之後第一次呼叫程式碼時，不會套用您的編輯，但是會在程式碼的所有後續呼叫中套用編輯。  
  
|||  
|-|-|  
|2001|找不到區域變數或變數資料類型已經變更: symbol \(*symbol*\)|  
|2002|已刪除的變數或新的區域變數需要建構或解構: symbol \(*symbol*\)|  
|2004|無法處理加入或移除名稱已經定義一次以上的區域變數: symbol \(*symbol*\)|  
  
##  <a name="BKMK_OtherActionRequiredMessages"></a> 需要執行其他動作的訊息  
 訊息文字後面會描述解決這些訊息所需執行的動作。  
  
|||  
|-|-|  
|2007|無法移除某些在反組譯碼視窗所設定的中斷點。<br /><br /> 若要解決這個問題，請重設受影響的中斷點。|  
|2008|無法載入檔案 *file* \(於模組 *module* 中\) 的偵錯符號。<br /><br /> 若要解決這個問題，請使用目前的 [!INCLUDE[vs_current_short](../misc/includes/vs_current_short_md.md)] 版本重建指定的模組。|  
  
## 請參閱  
 [編輯後繼續 \(Visual C\+\+\)](../Topic/Edit%20and%20Continue%20\(Visual%20C++\).md)   
 [編輯後繼續](../Topic/Edit%20and%20Continue.md)