---
title: "硬體例外狀況 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "錯誤 [C++], 硬體"
  - "錯誤 [C++], 低層級"
  - "例外狀況, 硬體"
  - "硬體例外狀況"
  - "低層級錯誤"
ms.assetid: 06ac6f01-a8cf-4426-bb12-1688315ae1cd
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 硬體例外狀況
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

大部分可由作業系統辨識的標準例外狀況是硬體定義的例外狀況。  Windows 可辨識某些低階軟體例外狀況，不過，作業系統通常最適合處理這些例外狀況。  
  
 Windows 會將不同的處理器硬體錯誤對應到本節中的例外狀況代碼。  在某些情況下，處理器可能只會產生這些例外狀況的子集。  有關例外狀況以及發出適當例外狀況代碼的 Windows 前置處理資訊。  
  
 下表摘要說明 Windows 所辨識的硬體例外狀況：  
  
|例外狀況代碼|例外狀況的原因|  
|------------|-------------|  
|**STATUS\_ACCESS\_VIOLATION**|讀取或寫入無法存取的記憶體位置。|  
|**STATUS\_BREAKPOINT**|遇到硬體定義的中斷點，只能由偵錯工具使用。|  
|**STATUS\_DATATYPE\_MISALIGNMENT**|在未正確對齊的位址讀取或寫入資料，例如，16 位元的實體必須在 2 個位元組的界限上對齊。\(不適用於 Intel 80*x*86 處理器\)。|  
|**STATUS\_FLOAT\_DIVIDE\_BY\_ZERO**|除以 0.0 的浮點類型。|  
|**STATUS\_FLOAT\_OVERFLOW**|超出浮點類型的最大正數。|  
|**STATUS\_FLOAT\_UNDERFLOW**|超出浮點類型的最小負數範圍。|  
|**STATUS\_FLOATING\_RESEVERED\_OPERAND**|使用保留的浮點格式 \(使用無效的格式\)。|  
|**STATUS\_ILLEGAL\_INSTRUCTION**|嘗試執行處理器未定義的指令碼。|  
|**STATUS\_PRIVILEGED\_INSTRUCTION**|執行目前電腦模式中不允許的指令。|  
|**STATUS\_INTEGER\_DIVIDE\_BY\_ZERO**|除以 0 的整數類型。|  
|**STATUS\_INTEGER\_OVERFLOW**|嘗試進行超過整數範圍的作業。|  
|**STATUS\_SINGLE\_STEP**|在單一步驟模式中執行一個指令，只能由偵錯工具使用。|  
  
 上表中列出的許多例外狀況主要是要由偵錯工具、作業系統，或其他低階程式碼處理。  除了整數和浮點數的錯誤之外，您的程式碼不應該處理這些錯誤。  因此，您通常應該使用例外狀況處理篩選條件來忽略例外狀況 \(運算結果為 0\)。  否則，您可以透過適當的回應來防止低階機制執行。  不過，您可以藉由[撰寫終止處理常式](../cpp/writing-a-termination-handler.md)，針對這些低階錯誤的潛在影響採取適當的措施。  
  
## 請參閱  
 [撰寫例外狀況處理常式](../cpp/writing-an-exception-handler.md)   
 [結構化例外狀況處理](../cpp/structured-exception-handling-c-cpp.md)