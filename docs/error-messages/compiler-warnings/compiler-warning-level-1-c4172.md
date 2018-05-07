---
title: 編譯器警告 （層級 1） C4172 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4172
dev_langs:
- C++
helpviewer_keywords:
- C4172
ms.assetid: a8d2bf65-d8b1-4fe3-8340-a223d7e7fde6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 746442638820d0c81144611a678996dc4c8483b0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4172"></a>編譯器警告 （層級 1） C4172
傳回區域變數或暫存的位址  
  
 函數會傳回本機變數或暫存物件的位址。 本機變數和暫存物件被終結函式傳回時，因此傳回的位址無效。  
  
 重新設計函式，讓它不會傳回本機物件的位址。  
  
 下列範例會產生 C4172:  
  
```  
// C4172.cpp  
// compile with: /W1 /LD  
float f = 10;  
  
const double& bar() {  
// try the following line instead  
// const float& bar() {  
   return f;   // C4172  
}  
```