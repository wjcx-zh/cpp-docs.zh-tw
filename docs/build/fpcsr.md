---
title: FpCsr |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: dff95d5d-7589-4432-82db-64b459c24352
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9defb41a026b32acb4375185f14c903788b91a23
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367442"
---
# <a name="fpcsr"></a>FpCsr
暫存器狀態也包含將 x87 FPU 控制字組。 呼叫慣例會要求此暫存器為靜態。  
  
 將 x87 FPU 控制字組暫存設定為下列的標準值開頭的程式執行：  
  
```  
FPCSR[0:6]: Exception masks all 1's (all exceptions masked)  
FPCSR[7]: Reserved - 0  
FPCSR[8:9]: Precision Control - 10B (double precision)  
FPCSR[10:11]: Rounding  control - 0 (round to nearest)  
FPCSR[12]: Infinity control - 0 (not used)  
```  
  
 修改任何 fpcsr 欄位被呼叫端必須將它們還原後再傳回至呼叫端。 此外，已修改這些欄位的呼叫端必須還原為其標準的值之前叫用被呼叫端，除非協議由被呼叫端必須要有修改過的值。  
  
 有兩個例外控制旗標不適用規則：  
  
1.  在指定的函式的目的為修改靜態 FpCsr 函式加上旗標。  
  
2.  時，它可以證明更正這些規則的違規情形，會導致程式的行為/意義和這些規則不違反規則的程式，例如，透過分析整個程式相同。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫慣例](../build/calling-convention.md)