---
title: "struct UNWIND_INFO | Microsoft Docs"
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
ms.assetid: f0aee906-a1b9-44cc-a8ad-463637bd5411
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# struct UNWIND_INFO
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

回溯資料資訊結構是用來在堆疊指標上記錄函式的效果，也是靜態暫存器在堆疊上儲存的位置：  
  
|||  
|-|-|  
|UBYTE: 3|版本|  
|UBYTE: 5|旗標|  
|UBYTE|初構的大小|  
|UBYTE|回溯程式碼的數目|  
|UBYTE: 4|框架暫存器|  
|UBYTE: 4|框架暫存器位移 \(已調整\)|  
|USHORT \* n|回溯程式碼陣列|  
|variable|可以為以下的形式 \(1\) 或 \(2\)|  
  
 \(1\) 例外處理常式  
  
|||  
|-|-|  
|ULONG|例外狀況處理常式的位址|  
|variable|語言特定處理常式資料 \(選擇性\)|  
  
 \(2\) 鏈結的回溯資訊  
  
|||  
|-|-|  
|ULONG|函式開始位址|  
|ULONG|函式結束位址|  
|ULONG|回溯資訊位址|  
  
 UNWIND\_INFO 結構在記憶體中必須對齊 DWORD。  每個欄位的意義如下：  
  
 **版本**  
 回溯資料的版本號碼，目前為 1。  
  
 **旗標**  
 目前定義了三個旗標：  
  
 UNW\_FLAG\_EHANDLER 函式不應該呼叫，以尋找函式時必須檢查例外狀況的例外處理常式。  
  
 UNW\_FLAG\_UHANDLER 函式不應該呼叫，在回溯例外狀況時的終止處理常式。  
  
 這個回溯資訊結構的 UNW\_FLAG\_CHAININFO 不是主要的程序的。  相反地，鏈結的回溯資訊項目是前一個 RUNTIME\_FUNCTION 項目的內容。  請參閱下列說明文字，了解鏈結的回溯資訊結構。  如果設定這個旗標，則 UNW\_FLAG\_EHANDLER 和 UNW\_FLAG\_UHANDLER 旗標必須清除。  此外，框架暫存器和固定的堆疊配置欄位，必須具有和主要回溯資訊相同的值。  
  
 **初構的大小**  
 函式初構的長度，以位元組為單位。  
  
 **回溯程式碼的數目**  
 這是回溯程式碼陣列中位置的數目。  請注意某些回溯程式碼 \(例如 UWOP\_SAVE\_NONVOL\) 會需要陣列中一個以上的位置。  
  
 **框架暫存器**  
 如果不為零，則函式會使用框架指標，而這個欄位則是做為框架指標之靜態暫存器的數目，並使用和 UNWIND\_CODE 節點的作業資訊欄位相同的編碼方式。  
  
 **框架暫存器位移 \(已調整\)**  
 如果框架暫存器欄位不為零，則這是在 FP 暫存器建立時套用至 FP 暫存器之已調整的 RSP 位移。  真正的 FP 暫存器會設定為 RSP \+ 16 \* 這個數字，允許從 0 到 240 的位移。  這可以將 FP 暫存器指向區域堆疊配置的中間以提供動態堆疊框架，經由較短的指令達成較佳的程式碼密度 \(較多指令可以使用 8 位元有號位移的形式\)。  
  
 **回溯程式碼陣列**  
 這是項目的陣列，其中的項目會說明初構對靜態暫存器和 RSP 的作用。  如需個別項目的意義，請參閱 UNWIND\_CODE 章節。  基於對齊的目的，這個陣列永遠會有偶數個項目，而最後項目可能不使用 \(此種情況下，陣列的元素會比回溯程式碼數目欄位所表示的還要多一個\)。  
  
 **例外狀況處理常式的位址**  
 這是相對於影像的指標，指向函式的語言特定例外狀況\/終止處理常式 \(如果旗標 UNW\_FLAG\_CHAININFO 已清除且 UNW\_FLAG\_EHANDLER 或 UNW\_FLAG\_UHANDLER 旗標已設定\)。  
  
 **語言特定處理常式資料**  
 這是函式的語言特定例外狀況處理常式資料。  這個資料的格式是未指定的，而且完全由使用的特定例外狀況處理常式來決定。  
  
 **鏈結的回溯資訊**  
 如果旗標 UNW\_FLAG\_CHAININFO 已設定，則 UNWIND\_INFO 結構會以三個 UWORD 結束。  這些 UWORD 表示鏈結之回溯的函式之 RUNTIME\_FUNCTION 資訊。  
  
## 請參閱  
 [回溯資料以進行例外狀況處理與偵錯工具支援](../build/unwind-data-for-exception-handling-debugger-support.md)