---
title: "編譯器警告 （層級 3） C4554 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4554
dev_langs: C++
helpviewer_keywords: C4554
ms.assetid: 55bb68f0-2e80-4330-8921-51083c4f8d53
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 063c317e25be808c14b65c08fe005bbbac7109e4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4554"></a>編譯器警告 (層級 3) C4554
'operator': 檢查運算子優先順序找出可能發生的錯誤。使用括號釐清順序  
  
 下列範例會產生 C4554:  
  
```  
// C4554.cpp  
// compile with: /W3 /WX  
int main() {  
   int a = 0, b = 0, c = 0;  
   a = a << b + c;   // C4554  
   // probably intended (a << b) + c,  
   // but will get a << (b + c)  
}  
```