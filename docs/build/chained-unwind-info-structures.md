---
title: "鏈結的回溯資訊結構 | Microsoft Docs"
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
ms.assetid: 176835bf-f118-45d9-9128-9db4b7571864
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 鏈結的回溯資訊結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果設定了 UNW\_FLAG\_CHAININFO 旗標，則回溯資訊結構會是次要資訊，而共用的例外狀況\-處理常式\/鏈結\-資訊地址欄位會包含主要回溯資訊。  下列程式碼會擷取主要回溯資訊，並假設 `unwindInfo` 是設定了 UNW\_FLAG\_CHAININFO 旗標的結構。  
  
```  
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);  
```  
  
 鏈結資訊在下列兩種情況中非常有用。  首先，它可以用在非連續的程式碼區段。  透過利用鏈結的資訊，您可以減少必要回溯資訊的大小，因為不需從主要回溯資訊複製回溯程式碼陣列。  
  
 您也可以使用鏈結的資訊來群組暫存器儲存的 volatile。  編譯器可以延遲儲存某些變動暫存器，直到函式項目初構超出範圍為止。  若要記錄此動作，可以讓函式部分的主要回溯資訊出現在群組程式碼之前，再將鏈結資訊設定為非零的初構大小，其中鏈結資訊的回溯程式碼反映了靜態暫存器的儲存動作。  在該情況中，回溯程式碼將會全部是 UWOP\_SAVE\_NONVOL 的執行個體。  無法儲存靜態暫存器使用推入或修改 RSP 暫存器使用一個固定堆疊配置的群組不支援。  
  
 設定 UNW\_FLAG\_CHAININFO 的 UNWIND\_INFO 項目可以包含 RUNTIME\_FUNCTION 項目，其 UNWIND\_INFO 項目也設定了 UNW\_FLAG\_CHAININFO 設定 \(多個壓縮包裝\)。  最後，鏈結的回溯資訊指標會到達 UNWIND\_INFO 項目 \(UNW\_FLAG\_CHAININFO 已清除\)，它就是指向實際程序進入點 \(Entry Point\) 的主要 UNWIND\_INFO 項目。  
  
## 請參閱  
 [回溯資料以進行例外狀況處理與偵錯工具支援](../build/unwind-data-for-exception-handling-debugger-support.md)