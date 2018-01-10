---
title: "編譯器警告 （層級 1） C4581 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4581
dev_langs: C++
helpviewer_keywords: C4581
ms.assetid: 598bcd87-257d-4eb3-94e4-15bb31aadc99
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 59bf4eafe722283f5fced046e845c6b46ca3ce82
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4581"></a>編譯器警告 (層級 1) C4581
已被取代的行為: '"string1"' 取代 'string2' 處理序屬性  
  
 針對 Visual c + + 2005年所進行的編譯器一致性工作可能會導致這個錯誤： 檢查 Visual c + + 屬性的參數。  
  
 在舊版中，不論以引號括住接受屬性值。 值是列舉型別，就必須不被括在引號內。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4581。  
  
```  
// C4581.cpp  
// compile with: /c /W1  
#include "unknwn.h"  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyI : IUnknown {};  
  
[coclass, uuid(12345678-1111-2222-3333-123456789012), threading("free")]   // C4581  
// try the following line instead  
// [coclass, uuid(12345678-1111-2222-3333-123456789012), threading(free)]  
class CSample : public IMyI {};  
```