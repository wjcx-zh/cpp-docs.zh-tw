---
title: 編譯器錯誤 C2040 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2040
dev_langs:
- C++
helpviewer_keywords:
- C2040
ms.assetid: 74ca3592-1469-4965-ab34-a4815e2fbefe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6b19a5dd647e51efb46ef9798b7f7cdff5339b9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167537"
---
# <a name="compiler-error-c2040"></a>編譯器錯誤 C2040
'operator' : 'identifier1' 在間接層級中不同於 'identifier2'  
  
 牽涉到指定之運算元的運算式具有不相容的運算元類型，或隱含地轉換運算元類型。 如果這兩個運算元都是算術或兩者都是非算術 (例如陣列或指標)，則會使用它們且不會變更。 如果有一個運算元是算術，而另一個不是，則算術運算元會轉換成非算術運算元的類型。  
  
 此範例也會產生 C2040，並顯示如何修正它。  
  
```  
// C2040.cpp  
// Compile by using: cl /c /W3 C2040.cpp  
bool test() {  
   char c = '3';  
   return c == "3"; // C2446, C2040  
   // return c == '3'; // OK  
}  
```