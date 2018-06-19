---
title: 編譯器警告 （層級 1） C4581 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4581
dev_langs:
- C++
helpviewer_keywords:
- C4581
ms.assetid: 598bcd87-257d-4eb3-94e4-15bb31aadc99
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 415fb9ffc3e53ddfe9edcee2ec99361b38de0dea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281855"
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