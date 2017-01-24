---
title: "struct RUNTIME_FUNCTION | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 84386527-d3aa-41c5-871d-78e3e1913704
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# struct RUNTIME_FUNCTION
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表格架構的例外狀況處理 \(Exception Handling\) 需要所有配置堆疊空間或呼叫另一個函式 \(例如非分葉的函式\) 之函式的表格項目。  函式表項目格式為：  
  
|||  
|-|-|  
|ULONG|函式開始位址|  
|ULONG|函式結束位址|  
|ULONG|回溯資訊位址|  
  
 RUNTIME\_FUNCTION 結構在記憶體中必須對齊 DWORD。  所有的位址是相對於影像的，也就是說，是從包含函式表項目之影像開始位址計算的 32 位元位移 \(Offset\)。  這些項目是已排序的，並放置於 PE32\+ 影像的 .pdata 區段。  對於動態產生的函式 \(JIT 編譯器\)，支援這些函式的執行階段必須使用 RtlInstallFunctionTableCallback 或 RtlAddFunctionTable，將這項資訊提供給作業系統。  如果無法提供這項資訊，會導致不可靠的例外狀況處理和處理序 \(Process\) 偵錯。  
  
## 請參閱  
 [回溯資料以進行例外狀況處理與偵錯工具支援](../build/unwind-data-for-exception-handling-debugger-support.md)