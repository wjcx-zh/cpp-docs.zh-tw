---
title: "MxCsr | Microsoft Docs"
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
ms.assetid: 4f3c229d-0862-4733-acc7-9ed7a0b870ce
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# MxCsr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

暫存器狀態也包括 MxCsr。  呼叫慣例會將這個暫存器分為動態部分和靜態部分。  動態部分由 6 個狀態旗標組成 \(MXCSR\[0:5\]\)，而暫存器剩下的部分 \(MXCSR\[6:15\]\) 則視為靜態。  
  
 靜態部分在程式執行開始時會設定為下列標準值：  
  
```  
MXCSR[6]         : Denormals are zeros - 0  
MXCSR[7:12]      : Exception masks all 1's (all exceptions masked)  
MXCSR[13:14]   : Rounding  control - 0 (round to nearest)  
MXCSR[15]      : Flush to zero for masked underflow - 0 (off)  
```  
  
 修改任何 MXCSR 靜態欄位的被呼叫端，必須在傳回至呼叫端之前將欄位還原。  此外，已修改這些欄位的呼叫端，必須在叫用被呼叫端之前將欄位還原為標準值，除非雙方同意被呼叫端會有已修改的值。  
  
 控制旗標的靜態規則有兩種不適用的例外情況：  
  
-   在給定函式的設計目的就是為了要修改靜態 MxCsr 旗標的函式中。  
  
-   當違反這些規則會使程式的行為\/意義和未違反規則的程式一樣 \(例如經由整體程式分析\) 的時候。  
  
 您不能在不同的函式之間對 MXCSR 動態部分的狀態做任何假設，除非函式的說明文件中特別描述。  
  
## 請參閱  
 [呼叫慣例](../build/calling-convention.md)