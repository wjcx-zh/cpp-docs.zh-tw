---
title: "FpCsr | Microsoft Docs"
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
ms.assetid: dff95d5d-7589-4432-82db-64b459c24352
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# FpCsr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

暫存器狀態也包括 x87 FPU 控制字組。  呼叫慣例會要求這個暫存器為靜態。  
  
 x87 FPU 控制字組暫存器在程式執行開始時會設定為下列標準值：  
  
```  
FPCSR[0:6]: Exception masks all 1's (all exceptions masked)  
FPCSR[7]: Reserved – 0  
FPCSR[8:9]: Precision Control – 10B (double precision)  
FPCSR[10:11]: Rounding  control - 0 (round to nearest)  
FPCSR[12]: Infinity control – 0 (not used)  
```  
  
 修改任何 FPCSR 欄位的被呼叫端，必須在傳回至呼叫端之前將資料還原。  此外，已修改這些欄位的呼叫端，必須在叫用被呼叫端之前將欄位還原為標準值，除非雙方同意被呼叫端會有已修改的值。  
  
 控制旗標的靜態規則有兩種不適用的例外情況：  
  
1.  設計目的就是為了要修改靜態 FpCsr 旗標的函式。  
  
2.  當違反這些規則會使程式的行為\/意義和未違反規則的程式一樣 \(例如經由整體程式分析\) 的時候。  
  
## 請參閱  
 [呼叫慣例](../build/calling-convention.md)