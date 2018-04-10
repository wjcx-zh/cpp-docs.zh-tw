---
title: 沒有原型的函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: 34200b8c-5b52-4f0d-aff8-9f70d82868ed
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 574c4564394e251dde9345d3658304019dae838d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="unprototyped-functions"></a>沒有原型的函式
對於完全原型的函式，呼叫端會傳遞整數值以整數和浮點數的值做為雙精確度。 僅限浮點值，整數暫存器和浮點暫存器將會包含浮點值萬一被呼叫端必須是整數暫存器中的數值。  
  
```  
func1();  
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7  
   func1(2, 1.0, 7);  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [呼叫慣例](../build/calling-convention.md)