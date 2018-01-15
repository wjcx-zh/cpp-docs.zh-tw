---
title: "MxCsr |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 4f3c229d-0862-4733-acc7-9ed7a0b870ce
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7794cea8906440c0adca94791d08e3ced6af747e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mxcsr"></a>MxCsr
暫存器狀態也會包含 MxCsr。 呼叫慣例會將此暫存器分割為變動性部分與靜態部分。 動態部分所組成的 6 的狀態旗標，MXCSR [0:5]，而 MXCSR [6:15] 暫存器的其餘部分會被視為靜態。  
  
 靜態部分是在程式執行開始設定為下列的標準值：  
  
```  
MXCSR[6]         : Denormals are zeros - 0  
MXCSR[7:12]      : Exception masks all 1's (all exceptions masked)  
MXCSR[13:14]   : Rounding  control - 0 (round to nearest)  
MXCSR[15]      : Flush to zero for masked underflow - 0 (off)  
```  
  
 修改任何 mxcsr 的靜態欄位被呼叫端必須將它們還原後再傳回至呼叫端。 此外，已修改這些欄位的呼叫端必須還原為其標準的值之前叫用被呼叫端，除非協議由被呼叫端必須要有修改過的值。  
  
 有兩個例外控制旗標不適用規則：  
  
-   在指定的函式的目的為修改靜態 MxCsr 函式加上旗標。  
  
-   時，它可以證明更正這些規則的違規情形，會導致程式的行為/意義和這些規則不違反規則的程式，例如，透過分析整個程式相同。  
  
 除非特別函式的文件所述，您可以不進行任何假設不同的函式，MXCSR 動態部分的狀態。  
  
## <a name="see-also"></a>請參閱  
 [呼叫慣例](../build/calling-convention.md)